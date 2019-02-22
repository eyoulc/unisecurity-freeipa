# unisecurity-freeipa
背景：
    FreeIPA + Ranger是HDP推荐的安全加密系统。其中:
    FreeIPA是CentOS提供的，它是LDAP + Kerberos 的安全环境。
    Ranger是用户权限管理系统。
	

程序执行前提：
   FreeIPA与Ranger都已经搭建完成，且能够正常运行.

程序说明：
   程序通过Rest接口的方式，将用户写入到FreeIPA中，当完成再调用ranger的API接口将用户信息写入到Ranger中
   不能过Ranger自身的usersync的原因是：在0.70版本中，usersync只有在启动时，才会同步用户信息，因此只能通过定时执行usersync的方式，时效性太差。
   
缺点：
   1） Ranger用户无法删除。原因当前版本是基于Ranger 0.7.0，在这个版本中，api接口不支持删除
