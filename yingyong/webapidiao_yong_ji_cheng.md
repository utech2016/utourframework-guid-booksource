# 3.8 WebAPI调用集成
对WebApi调用和格式在框架中进行了统一封装，并提供了api接口数据缓存功能，具体使用请按照如下方式：
1. 直接依赖dll引入
  - Utour.Framework.Web.dll
  - Utour.Framework.CacheAccess.dll
  - Utour.Framework.CAInterface.dll
2. 加入两项配置文件
   WebApiAuth.config--api如有授权验证，则在调用方需加入此配置
   WebApiCache.config--在api服务层配置哪些接口需要进行结果缓存
3. 在api项目WebApiConfig类Register方法加入下面三行代码配置
```C#
  //注册全局接口缓存Filter，统一接口Json结果格式
  config.Filters.Add(new WebApiDataCacheFilterAttribute("damoapi.utour.com"));
  //注册全局接口异常Filter
  config.Filters.Add(new WebApiExceptionFilter());
  //清除默认xml接口默认格式，启用Json格式
  config.Formatters.Remove(config.Formatters.XmlFormatter);
 ```
4. 框架统一了每个API返回的Json格式，每个web api 返回值须是Utour.Framework.Web.DTO.APIDataResult类型对象，在返回时无需再Json序列化结果，框架内部会自动序列化并根据配置决定是否读取或写入缓存.

  APIDataResultl对象
```C#
     /// <summary>
    /// Web Api 统一返回JSON格式实体
    /// </summary>
    public class APIDataResult
    {
        public APIDataResult()
        { 
        
        }
        /// <summary>
        /// APIDataResult 构造函数初始化
        /// </summary>
        /// <param name="errorCode">操作代码</param>
        /// <param name="errMsg">错误提示</param>
        /// <param name="jsonResult">操作结果，JSON格式</param>
        public APIDataResult(int errorCode,string errMsg,string jsonResult)
        {
            this.ErrorCode=errorCode;
            this.ErrorMsg = errMsg;
            this.JsonResult = jsonResult;
        }

        /// <summary>
        /// ErrorCode
        /// 200：成功
        /// -1：系统错误信息
        /// -2：自定义错误信息
        /// </summary>
        public int ErrorCode { get; set; }

        /// <summary>
        /// 错误信息
        /// </summary>
        public string ErrorMsg { get; set; }

        /// <summary>
        /// JSON数据结果
        /// </summary>
        public string JsonResult { get; set; }
    }
 ```
 Web API接口示例代码：
 ```C#
     public class UsersController : ApiController
    {
        // GET api/users

        [HttpPost]
        public APIDataResult GetUserList()
        {
            IUserManageService ums = ServiceFactory.GetInstance<IUserManageService>();
            APIDataResult result = new APIDataResult();
            try
            {
               List<User> list = ums.GetUserList();
               result = new APIDataResult()
               {
                   ErrorCode = 200,
                   ErrorMsg = "获取成功",
                   JsonResult = JsonHelper.SerializeObject(list)
               };
            }
            catch (Exception)
            {
                result = new APIDataResult()
                {
                    ErrorCode=-2,
                    ErrorMsg = "接口错误",
                    JsonResult = JsonHelper.SerializeObject("")
                };
            }
            return result;
        }
    }
 ```
 
 5. 客户端调用，使用```Utour.Framework.Web.WebApiHepler```进行调用，如下
 
    ```C# 
     string api = "http://demoapi.utour.com";
     var jsonReq = "{\"Id\":" + 3 + "}";
     string jsonResult1 = WebApiHepler.RequestWebAPI(api, "users", "GetUserById", jsonReq , true);
     ```
