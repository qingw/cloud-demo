*_项目搭建_*：参考链接： http://blog.didispace.com/springcloud5/
服务网关是微服务架构的重要部分，是我们必须要去做的原因：
    1、不仅仅实现了路由功能来屏蔽诸多服务细节，更实现了服务级别、均衡负载的路由。
    2、实现了接口权限校验与微服务业务逻辑的解耦。通过服务网关中的过滤器，在各生命周期中去校验请求的内容，
        将原本在对外服务层做的校验前移，保证了微服务的无状态性，同时降低了微服务的测试难度，让服务本身更集中关注业务逻辑的处理。
    3、实现了断路器，不会因为具体微服务的故障而导致服务网关的阻塞，依然可以对外服务。


*外部应用申请获取 AccessToken
*通过 AccessToken 调用内部服务。
*内部服务之间的调用不需要 AccessToken

ZuulFilter 过滤器 与 OAuth2Interceptor 拦截器

当请求的服务未配置路由时，
处理逻辑：ZuulFilter 先处理，OAuth2Interceptor 后处理

当配置了路由时，
处理逻辑：只有 ZuulFilter 处理

拦截器+ZuulFilter
需注意事项 参考：http://stackoverflow.com/questions/39801282/handlerinterceptoradapter-and-zuul-filter
