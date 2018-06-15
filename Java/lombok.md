# lombok

Lombok是一个可以通过简单的注解形式来帮助我们简化消除一些必须有但显得很臃肿的Java代码的工具，通过使用对应的注解，可以在编译源码的时候生成对应的方法。

## 在IDEA中安装lombok插件件

1. 在IDEA中执行操作：File | Settings | Plugins，打开插件界面。
2. 单击 Browse repositoryes... 按钮，在弹出对话框中输入 lombok。
3. 从中找到 lombok 插件，下载安装。
4. 重启 IDEA，完成插件安装。

## 在项目中引入 lombok 的 jar 包

在 pom.xml 文件中增加以下代码：

```
 <dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.16.10</version>
    <scope>provided</scope>
</dependency>
```

## @Getter 和 @Setter

可以在类或方法上使用这2个注解，让 lombok 自动生成默认的 getter / setter 方法。默认生成的方法是public的。

## @toString

生成toString()方法，默认情况下，将按顺序类名称以及每个字段。
可以通过排除参数设置不包含哪些字段@ToString(exclude = "id") / @ToString(exclude = {"id","name"})
如果继承的有父类的话，可以设置callSuper 让其调用父类的toString()方法，例如：@ToString(callSuper = true)

## @EqualsAndHashCode

生成 hashCode() 和 equals() 方法，默认情况下，它将使用所有非静态，非transient字段。但可以通过在可选的exclude参数中来排除更多字段。或者，通过在parameter参数中命名它们来准确指定希望使用哪些字段。

## @NoArgsConstructor

生成一个无参构造方法。

## @RequiredArgsConstructor

生成构造方法（可能带参数也可能不带参数），如果带参数，这参数只能是以final修饰的未经初始化的字段，或者是以@NonNull注解的未经初始化的字段

## @RequiredArgsConstructor(staticName = "of")

生成一个of()的静态方法，并把构造方法设置为私有的

## @Data

@Data 包含了 @ToString、@EqualsAndHashCode、@Getter / @Setter和@RequiredArgsConstructor的功能

## @Slf4j

使用了该注解，不用写private  final Logger log = LoggerFactory.getLogger(XXX.class); 

可直接在代码中使用log进行日志的输出，如：
```
log.debug("debug message");
log.warn("warn message");
log.info("info message");
log.error("error message");
log.trace("trace message");
```

注意：如果在类上添加注解@Slf4j后找不到变量log，说明IDE中未安装lombok插件。