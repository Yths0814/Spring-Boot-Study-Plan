# Spring Boot Study-Plan
Fighting!

### 计划 
1. 安装好IDEA,MySQL,配置好环境。初步了解IDEA。
2. 跟着教程导入项目，运行起来。
3. 多跑几个项目，总结步骤，细化每一个步骤。
4. 扎实基础，学习Spring Boot 
5. 学习Maven 多模块项目。
6. https://accp.site/categories/%E7%BC%96%E7%A8%8B/Java/SpringBoot/ 学习Spring Boot基础
---

## 进度
---
#### The first day(10.12)
1. 注册并学会使用GitHub，了解markdown语法。
2. 下载安装配置IntelliJ IDEA

---
#### The second day(10.13)
- [x] 学习markdown语法
- [x] maven本地配置，配置镜像加速maven加载速度。
- [x] 安装tomcat，配置环境变量，IDEA配置tomcat
- [x] 在IDEA创建简单Web项目并运行。
- [x] 学习GitHub协同合作，Fork后进行自己的修改，pull request进行更新和提交自己的修改到源项目，参与项目和让项目得到更好的发展。
- [ ] 学习比较齐全的IDEA介绍，包括新建项目等。 https://github.com/judasn/IntelliJ-IDEA-Tutorial
- [ ] 导入了项目 ssm-demo,还没有跑起来。

---
#### The third day(10.14)
- [x] 安装MySQL
- [x] 学习IDEA介绍：基础设置（包括UI界面），索引和编译方式，了解但未背诵快捷键
- [x] Maven单模块 Spring MVC + Spring + Mybatis 的demo尝试
> 数据库连接
> 数据库初始化
> 单元测试出错，未解决问题 

---
#### The fourth day(10.15)
- [x] 运行起<https://github.com/ZHENFENG13/ssm-demo>的ssm_maven项目
![ssm_maven](https://github.com/Yths0814/picture/blob/master/images/ssm_maven.png)
````
今天运行 ssm_maven 时以 tomcat build 项目，一开始一直不成功，
后来是因为项目得配置要求Tomcat7.0，而我的IDEA用的时Tomcat9.0，
后来重新配了一下就运行起来了。版本得出错也要注意。
````
---
#### The fifth day(10.16)
- [X] 上课间隙看了一些 spring boot 的基本概念知识。了解项目目录结构，主要是java,resources和test

- [X] 《SpringBoot学习目录》<http://blog.csdn.net/xuforeverlove/article/details/89635888> 详细基础，容易入门。

````
IDEA跑项目我的步骤：
> 导入项目
> maven(w我是手动配置)
> Database, new 一个schema, 然后给自己的数据库命名
> 运行数据库脚本，记得勾选上一步新建的数据库命，把表建在自己新建的数据库里
> 测试，会出错
> 以tomcat build 项目，web项目会自动弹出页面
````
---
#### The sixth day(10.17)
- [x] <https://github.com/judasn/Basic-Single-Module-SSM> 运行起 Maven单模块 Spring MVC + Spring + Mybatis 项目
![Basic-Single-Module-SSM](https://github.com/Yths0814/picture/blob/master/images/Basic-Single-Module-SSM.png)
 
  解决之前单元测试不通过问题，是因为MySQL版本问题。
- [x] 项目设置：JDK设置；Facet 加入 Spring（还不是很理解）
- [x] 代码相关
> 简单了解pom.xml文件
> 用InteliJ IDEA 的 Database 初始化数据库
> 单元测试（数据库版本问题导致第三天单元测试不通过，更改后成功连接数据库，单元测试通过）
> 启动 Tomcat 加上 Make Project 事件
> 访问 Controller 了解 Debug
> 静态资源映射，比如做图片上传等，如没有映射好可能遇到404
- [ ] MyBatis插件的使用

---
#### 10.21
- [x] 添加Banner文件
- [x] 创建Controller类，不同的注解方式

   ````
   1. @RestController:处理http请求：等同于@Controller +  @ResponseBody
   2. @RequestMapping:value = “访问的路由”method = 请求方法
   3. @GetMapping:以GET方式请求 相当于对@RequestMapping配置的缩写
   ````
- [x] URL的其他形式
     1.  窄化请求：类和方法都有value (http://localhost:8080/user/hello)
       ![](https://github.com/Yths0814/picture/blob/master/images/url.png)
     2. 配置多url对1映射 http://localhost:8080/hello 或 http://localhost:8080/hi
     
- [x] 其他项目创建方式
    1. > SPRING INITIALIZR：通过IDEA或者STS工具创建INITIALIZR项目
    
    2. >创建Maven项目手动添加依赖
        ````
        <parent>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-parent</artifactId>
            <version>1.5.9.RELEASE</version>
        </parent>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-starter-web</artifactId>
            </dependency>
        </dependencies>
        ````
     3. >通过https://start.spring.io/  生成定制项目
 
- [x] 运行方式
    * 在IDEA中直接运行
    * 发布jar包运行
        ````
        <!-- 这个插件，可以将应用打包成一个可执行的jar包；-->
           <build>
               <plugins>
                   <plugin>
                       <groupId>org.springframework.boot</groupId>
                       <artifactId>spring-boot-maven-plugin</artifactId>
                   </plugin>
               </plugins>
           </build>
        ````
        导入这个maven插件，利用idea打包，生成的jar包，可以使用java -jar xxx.jar启动
        
        Spring Boot 使用嵌入式的Tomcat无需再配置Tomcat
- [ ] Basic-Multi-Module-SSM项目运行成功，简单了解多模块项目构建方式。
---
#### 10.22
- [x] 参数传递
    ````
    1、get方式Url传参
    @PathVariable  http://localhost:8080/hello/Yt
    @RequestParam  http://localhost:8080/hello?name=Yt
    @RequestParam+默认参数 @RequestParam(value = "name",defaultValue = "admin")
    @RequestParam(value = "name",required=false)非必须参数

    ````
    
    ````
    2、post方式传递数据
    ````
 ---
#### 10.23
- [x] Getter and Setter方法太方便了，快捷键alt+insert
- [x] 学习配置文件：application.properties 和 application.yml
- [x] YMAL语法：基本语法和值的写法
- [x] 配置文件值注入
   1.  配置文件处理器
   
         ![](https://github.com/Yths0814/picture/blob/master/images/%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%E7%BB%91%E5%AE%9A.png)
    
   2.  @Value获取值和@ConfigurationPropeties获取值比较
    ````
    注：properties配置文件在IDEA中默认utf-8可能会乱码
    ````
---
#### 10.24
- [x] @PropertiesSource & @ImportResource
    ````
    @PropertiesSource 加载指定的配置文件
    @ImportResource 导入Spring的配置文件，让配置文件里的内容生效
    ````
- [x] Spring Boot 推荐给容器中添加组件的方式：推荐使用全注解的方式
    > 配置类中用@Bean 给容器添加组件
- [x] 配置文件占位符
- [x] Profile文件
    ````
    Profile是Spring对不同环境提供的不同配置功能的支持，可以通过激活、指定参数等方式快速切换环境。
    ````
- [x] 激活指定profile
    1. 在application.properties中指定spring.profiles.active=dev
    2. 在application.yml中用多文档块方式
    3. 命令行方式
    4. 虚拟机参数
---
#### 10.26
- [x] 返回json数据

    ![](https://github.com/Yths0814/picture/blob/master/images/返回json数据.png)
       
   ````
     Rather than relying on a view technology to perform server-side rendering of the 
     greeting data to HTML,this RESTful web service controller simply populates and 
     returns a Greeting object.The object data will be written directly to the HTTP 
     response as JSON.
    ````
- [x] IntelliJ Idea SpringBoot 数据库增删改查实例.

    ![](https://github.com/Yths0814/picture/blob/master/images/增删改查.png)
    
    实现了查找数据表并以json格式返回数据
    
    1. 创建与数据表对应的实体类
    2. 运行项目后，查看数据库，会自动创建表 ，接下来就可以进行表的增删改查了
    3. 创建控制器
    4. 创建一个接口，位于dao包下,调用该接口继承自JpaRepository的方法，来实现和数据库交互
    
---
#### 10.27
- [ ] 尝试IDEA+Maven 整合SSM框架实现简单的增删改查，还没成功。

    遇到的问题：创建Maven项目Unable to import maven projects
    
---
#### 10.28
- [x] 成功尝试IDEA+Maven 整合SSM框架实现简单的增删改查，实现一个前端小界面，可进行增删改查      
     
     ![](https://github.com/Yths0814/picture/blob/master/images/数据页.png)
     
     ![](https://github.com/Yths0814/picture/blob/master/images/增加数据.png)
     
     代码不是自己敲的，是自己一点点实现的，遇到很多很多问题，都是百度解决（忧愁）。接下来就是看看这个小集成页面的具体构成和代码。

- [x] 昨天遇到的Unable to import maven projects问题后来发现是因为maven版本问题。
- [x] 记得配置tomcat里的Deployment，添加war exploded不然会找不到 localhost 的网页。

---
#### 11、12月(实习)
- [x] 读取文档表格并以html格式输出(https://github.com/zavier/ReadWordTable.git)

- [x] 以Json格式输出数据
    ````
    {
    		"内部标识符":"HDSD00.03.040",
    		"数据元标识符（DE）":"DE08.10.052.00",
    		"数据元名称":"医疗机构组织机构代码",
    		"定义":"经《医疗机构执业许可证》登记的，并按照特定编码体系填写的代码",
    		"数据元值的数据类型":"S3",
    		"表示格式":"AN10",
    		"数据元允许值":"WS 218-2002"
    	},
    	{
    		"内部标识符":"HDSD00.03.025",
    		"数据元标识符（DE）":"DE01.00.010.00",
    		"数据元名称":"门（急）诊号",
    		"定义":"按照某一特定编码规则赋予门（急）诊就诊对象的顺序号",
    		"数据元值的数据类型":"S1",
    		"表示格式":"AN..18",
    		"数据元允许值":"—"
    	}
    	.....
    ````

- [x] 将读取的Json格式数据写入文件

- [ ] 表格表头，归类为数据集、数据元、值域

- [x] 部署项目

    ![](https://github.com/Yths0814/picture/blob/master/images/元数据平台.png)
    
#### 
- [x] 读取json文件的数据导入数据库。(电子病历基本数据集报批稿，数据元值域标准)

- [x] 元数据平台元数据管理模块代码熟悉

- [x] 元数据平台项目元数据管理模块界面的修改及功能的完善和调整。界面包括根据原型设计修改的搜索栏和关联界面，根据用户和使用角度添加了面包屑界面和操作列按钮，并以扩展行的形式展现。

- [x] 部署到测试环境，对bug进行修改，改bug的过程对部分功能进行完善 。


#### 个人总结
````
一、招聘会结束之后到实习开始之前的培训主要学习的内容在这里https://github.com/Yths0814/Spring-Boot-Study-Plan 主要是对SpringBoot的入门、环境配置、熟悉IDEA的使用以及如何跑项目。
 
二、开始实习主要的工作内容
1、编写程序实现读取文档表格并以json格式输出，导出为json文件。
2、将上一步的json文件中的数据导入数据库。导入了电子病历数据集报批稿17份文件和数据元值域标准。
3、了解元数据平台元数据管理模块的代码结构，弄清数据元，数据集和值域三者之间的关系。
4、元数据平台项目元数据管理模块界面的修改及功能的完善和调整。界面包括根据原型设计修改的搜索栏和关联界面，根据用户和使用角度添加了面包屑界面和操作列按钮，并以扩展行的形式展现。功能包括搜索框搜索功能的完善、编辑删除等基本CRUD操作。
5、部署到测试环境，对bug进行修改，改bug的过程对部分功能进行完善 。
6、主数据模块实体设计的主数据管理实现导出勾选的数据。
 
多熟悉现有的项目，方便以后的开发。在完成任务的同时一边学习，有自己的想法可以提出或者保留。在做这些工作的时候，因为是现有的项目，能够接触到的也是项目本身的东西，拥有一个很好的学习平台。暂时没有什么工作方面的疑惑。
 
三、存在不足
很多东西还需要学习。主要是加强业务知识学习，今后要认真总结经验，克服不足，把工作做好。感谢师兄和师傅以及同事的帮助，让我在这两个月的实习中有所成长。今后要更加努力学习，积累经验，提升自己。
 
四、规划
工作方面：首先跟着公司的发展目标认真完成自己的实习，希望自己可以胜任这个岗位，做好自己的本职工作，并在未来好好发展。未来工作包含以下三个目标：1、成果目标：掌握基本的业务知识，拥有较强的专业知识，在自己岗位做出一定的成果，团队中可以发挥自己的作用。 2、经济目标：拥有稳定工作。3、能力目标：（根据现有能力暂时还未规划）
技术方面：技术上应持续精进，上手或者熟练自己的工作内容后，不应待在舒适圈，考虑提升的点：项目优化、参与开源项目、进行输出。
生活方面：培养良好的生活习惯，持续学习。
````

- [x] Spring AOP的学习

- [x] Git学习
