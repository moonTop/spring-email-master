# spring-email-master
spring sends email by three methods

## 工具以及环境
    1 工具：Intellij Idea
    2 JDK：1.8
    3 Spring 4.3.4.release
    4 maven:3.x
## 项目结构
### src
     此项目是基于java的spring配置方式，下面介绍一个EmailApplicationContext这个配置类；
     EmailApplicationContext：实现的功能与<beans></beans>一样，定义方法返回实例，相当于xml中的<bean id="" class=""></bean>；
    
     config:主要是关于邮件配置，模板的配置，映射与properties文件；
     constant:定义一些常量；
     service:邮件发送的借口定义；
     type:邮件发送的类型，包括：简单的html，velocity模版， thymeleaf模版三种类型；
     vo:邮件信息的vo，包括，发件人，收件人，抄送人，密送人，邮件内容等；
### resource
     properties：资源文件
     velocity:velocity模版文件
     thymeleaf:thymeleaf模版文件
### test
     单元测试

### service方法介绍

    /**
     * 发送简单的文本格式
     *
     * @param vo
     */
    void sendEmailBySimpleText(EmailVO vo);

    /**
     * 发送html格式的消息
     *
     * @param vo
     */
    void sendEmailByHTMLText(EmailVO vo) throws Exception;

    /**
     * 发送邮件：简单文本或者HTML，附件
     *
     * @param vo
     */
    void sendEmailBySimpleTextAndAttachment(EmailVO vo, boolean isHtmlText) throws Exception;

    /**
     * velocity模版引擎发送
     *
     * @param vo
     */
    void sendEmailByVelocity(EmailVO vo) throws Exception;

    /**
     * thymeleaf模版引擎
     *
     * @param vo
     * @throws Exception
     */
    void sendEmailByThymeleaf(EmailVO vo) throws Exception;


    在实现方法中有大量的重复代码，下一步考虑使用模板方法进行重构，更加方便的支持多种方式邮件发送

    使使用者更加方便的使用

    现在只是简单的实现每种方式的发送的邮件，期待后续优化。
