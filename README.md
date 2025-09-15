## 关于 SpringDoc 说明

- 基于 `javadoc` 无注解零入侵生成规范的 `openapi` 结构体。

- 内部整合了Knife4j作为接口文档的可视化界面。

## 版本支持

springboot 2.x版本 请使用：1.0.3 

springboot 3.x版本 请使用：2.0.1 （感谢[张仕强](https://github.com/zhangslq)贡献支持Boot3版本的代码）

## 安装依赖

**Maven / Gradle**

SpringBoot 2 用这个：
```xml
		<dependency>
			<groupId>io.github.lvcongzheng520</groupId>
			<artifactId>springdoc</artifactId>
			<version>1.0.3</version>
		</dependency>
```

```bash
implementation group: 'io.github.lvcongzheng520', name: 'springdoc', version: '1.0.3'
```

SpringBoot 3 用这个：
```xml
		<dependency>
			<groupId>io.github.lvcongzheng520</groupId>
			<artifactId>springdoc</artifactId>
			<version>2.0.1</version>
		</dependency>
```

```bash
implementation group: 'io.github.lvcongzheng520', name: 'springdoc', version: '2.0.1'
```


## JavaDoc 插件准备

```xml
	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.9.0</version>
				<configuration>
					<source>${java.version}</source>
					<target>${java.version}</target>
					<encoding>${project.build.sourceEncoding}</encoding>
					<annotationProcessorPaths>
						<path>
							<groupId>com.github.therapi</groupId>
							<artifactId>therapi-runtime-javadoc-scribe</artifactId>
							<version>0.15.0</version>
						</path>
						<path>
							<groupId>org.projectlombok</groupId>
							<artifactId>lombok</artifactId>
							<version>${lombok.version}</version>
						</path>
						<path>
							<groupId>org.springframework.boot</groupId>
							<artifactId>spring-boot-configuration-processor</artifactId>
							<version>${springboot.version}</version>
						</path>
					</annotationProcessorPaths>
				</configuration>
			</plugin>
		</plugins>
	</build>
```

## application 配置

⚠️ 注意：packages-to-scan 每个项目的包结构命名不一样，请自行修改。

```yaml
# springdoc-openai 配置
springdoc:
  api-docs:
    # 是否开启接口文档
    enabled: true
    # OpenAPI文档的路径
    path: /v3/api-docs
  swagger-ui:
    # swagger-ui路径
    path: /swagger-ui.html
    # 持久化认证数据
    persistAuthorization: true
  info:
    # 标题
    title: '标题：SpringDoc后台管理系统_接口文档'
    # 描述
    description: '描述：用于管理集团旗下公司的人员信息,具体包括XXX,XXX模块...'
    # 版本
    version: '版本号: 1.0.0'
    # 作者信息
    contact:
      name: lcz
      email: 1926585708@qq.com
      url: https://gitee.com/hsqyz
  components:
    # 鉴权方式配置
    security-schemes:
      apiKey:
        type: APIKEY
        in: HEADER
        name: Authorization
  # 分组配置
  group-configs:
    - group: SpringDoc项目模块接口文档
      packages-to-scan: com.hsqyz
```

