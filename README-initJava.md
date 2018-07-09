# gradle
gradle使用指导


初始化Java项目.
	gradle -v
	gradle init
	gradle init --type java-library

	gradle clean	//清空编译目录
	gradle tasks	//查看所有task
	gradle javadoc	//查看javadoc所有task
	gradle assembleDebug 编译并打Debug包
	gradle assembleRelease 编译并打Release的包

	gradle build //构建命令
		gradle :compileJava	//编译Src中 Java文件
		gradle :processResources NO-SOURCE	//处理资源文件
		gradle :classes		//生成classes文件
			$ gradle class
				> Task :compileJava
				> Task :processResources NO-SOURCE
				> Task :classes

		gradle :jar		//生成Jar文件
			$ gradle jar
			> Task :compileJava
			> Task :processResources NO-SOURCE
			> Task :classes
			> Task :jar

		gradle :assemble	//打包装配debug和release的Jar
			$ gradle assemble
			> Task :compileJava
			> Task :processResources NO-SOURCE
			> Task :classes
			> Task :jar
			> Task :assemble

		gradle :compileTestJava		//编译测试文件
			$ gradle compileTestJava
			> Task :compileJava
			> Task :processResources NO-SOURCE
			> Task :classes
			> Task :compileTestJava

		gradle :processTestResources NO-SOURCE	//处理测试资源文件
		gradle :testClasses	//生成测试classes
			$ gradle testClasses
			> Task :compileJava
			> Task :processResources NO-SOURCE
			> Task :classes
			> Task :compileTestJava
			> Task :processTestResources NO-SOURCE
			> Task :testClasses

		gradle :test	//执行测试
			$ gradle test
			> Task :compileJava
			> Task :processResources NO-SOURCE
			> Task :classes
			> Task :compileTestJava
			> Task :processTestResources NO-SOURCE
			> Task :testClasses
			> Task :test

		gradle :check	//执行构建前检查
			$ gradle check
			> Task :compileJava
			> Task :processResources NO-SOURCE
			> Task :classes
			> Task :compileTestJava
			> Task :processTestResources NO-SOURCE
			> Task :testClasses
			> Task :test
			> Task :check

		gradle :build	//执行构建
			$ gradle build
			> Task :compileJava UP-TO-DATE
			> Task :processResources NO-SOURCE
			> Task :classes UP-TO-DATE
			> Task :jar
			> Task :assemble
			> Task :compileTestJava UP-TO-DATE
			> Task :processTestResources NO-SOURCE
			> Task :testClasses UP-TO-DATE
			> Task :test UP-TO-DATE
			> Task :check UP-TO-DATE
			> Task :build


	gradle copy	//复制目录
	gradle zip	//压缩目录
	gradle zip --scan	//压缩扫描目录
	gradle properties	//构建属性
	
	

settings.gradle文件配置：
	rootProject.name='building-java-libraries'


build.gradle文件配置：
	插件：	
		plugins {}
	依赖：
		dependencies {}
	仓库：
		repositories {jcenter() }

	版本：
		version = '0.1.0'
	Jar包：
		jar {
		    manifest {
			attributes('Implementation-Title': project.name,
				   'Implementation-Version': project.version)
		    }
		}


	