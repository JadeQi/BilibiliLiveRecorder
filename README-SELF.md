
### 
### 第一次打包
1. 修改pom文件
```xml
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-assembly-plugin</artifactId>
				<version>2.4.1</version>
				<configuration>
					<!-- get all project dependencies -->
					<descriptorRefs>
						<descriptorRef>jar-with-dependencies</descriptorRef>
					</descriptorRefs>
					<!-- MainClass in mainfest make a executable jar -->
					<archive>
						<manifest>
							<mainClass>nicelee.bilibili.Main</mainClass>
						</manifest>
					</archive>
				</configuration>
				<executions>
					<!-- 配置执行器 -->
					<execution>
						<id>make-assembly</id>
						<!-- 绑定到package命令的生命周期上 -->
						<phase>package</phase>
						<goals>
							<!-- 只运行一次 -->
							<goal>single</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
```
2. 性质META-INF文件, 文件路径放在 src路径下
3. 删除test文件 OR 点击Maven插件, 跳过测试模式
4. 先执行Maven -> 插件 -> jar -> jar:jar
5. 再执行Maven -> 生命周期 -> package. 会下载依赖. 如果在调用接口那就还有问题. 多重复几次 
6. jar包测试命令
    - java -Dfile.encoding=utf-8 -jar live-record-2.18.1-jar-with-dependencies.jar "debug=false&check=false&delete=false&liver=douyu&id=6667 43&qn=0&retry=5"