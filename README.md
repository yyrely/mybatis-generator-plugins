# mybatis-generator-plugins


## ExtPlugin
在Mapper接口类同级生成ext包,并生成对应的extMapper,继承mybatis generator生成Mapper,xmlMapper同理;达到平时开发修改Ext内容,防止再次使用mybatis generator生成文件被覆盖;

### 使用

- clone本项目
```
git clone git@github.com:ailinal/mybatis-generator-plugins.git
cd mybatis-generator-plugins
mvn install
```
- pom.xml
```xml
 <build>
        <plugins>
            <!--mybatis-generator插件-->
            <plugin>
                <groupId>org.mybatis.generator</groupId>
                <artifactId>mybatis-generator-maven-plugin</artifactId>
                <version>1.3.6</version>
                <configuration>
                    <verbose>true</verbose>
                    <overwrite>true</overwrite>
                </configuration>
                <dependencies>
                    <!--此处添加一个mysql-connector-java依赖可以防止找不到jdbc Driver-->
                    <dependency>
                        <groupId>mysql</groupId>
                        <artifactId>mysql-connector-java</artifactId>
                        <version>5.1.46</version>
                        <scope>runtime</scope>
                    </dependency>
                    <dependency>
                        <groupId>com.littmem.plugin</groupId>
                        <artifactId>mybatis-generator-plugins</artifactId>
                        <version>1.0.0.RELEASE</version>
                    </dependency>
                </dependencies>

            </plugin>

        </plugins>
    </build>
```
- generatorConfig.xml
```xml
 <plugin type="com.littmem.plugin.mybatis.generator.plugins.ExtPlugin"/>
```

## LombokPlugin
使生成的model添加lombok @Data注解;禁止setter getter方法生成; 