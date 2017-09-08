# 后端代码分层规约

基于平台开发的产品，以包前缀+业务模块+分层名，如com.yonyou.cloud.confcenter.service，建议组件下包划分如下： 

*	entity：业务实体
*	repository：持久化
*	service：服务层
*	web：web访问层
*	validate：业务校验
*	utils：工具类
*	common：通过代码
