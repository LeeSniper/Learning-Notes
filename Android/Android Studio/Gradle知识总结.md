# Gradle知识总结

## Module的build.gradle分解

	//说明这个build文件中使用Android plugin for Gradle
	//需要用到的plugin	
	apply plugin: 'com.android.application'  
	
	//配置所有针对Android项目build时的选项
	android {
	    compileSdkVersion 26	//编译时用的SDK版本，这样你的应用可以支持该版本及以下的新特性
	    buildToolsVersion "26.0.2"	//build工具的版本
	
		//动态在build时配置AndroidManifest.xml里的项目，可以覆盖manifest里的配置
	    defaultConfig {
	        applicationId "com.example.my.app"
	        minSdkVersion 15
	        targetSdkVersion 26
	        versionCode 1
	        versionName "1.0.0"
	    }
	    //配置如何构建和打包APP
	    buildTypes {
	        release {
	            minifyEnabled true
	            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
	        }
	    }
		//分渠道打包，可以配置不同版本，例如付费版，免费版
		productFlavors {
    		free {
      			applicationId 'com.example.myapp.free'
    		}

    		paid {
      			applicationId 'com.example.myapp.paid'
    		}
  		}
	}
	
	//在android{……}之外，此module的依赖
	dependencies {
	
	     // Module dependency 模块依赖，表示依赖于lib模块
	    compile project(":lib")
	
	    // Remote binary dependency 远程依赖
	    compile 'com.android.support:appcompat-v7:19.0.1'
	
	    // Local binary dependency //本地依赖，本地的jar包
	    compile fileTree(dir: 'libs', include: ['*.jar'])
	}


## 根目录里的build.gradle
定义所有module都适用的build配置

- buildscript 定义gradle自身的 repositories 和 dependencies 

- allprojects 定义所有module公用的 repositories 和 dependencies ，默认只添加了jcenter的repositories，没有定义 dependencies 依赖

- ext 包含其他一些所有module可以公用的属性。想要在子module里引用这些属性需要用 rootProject.ext.属性名。但是并不建议这么做，因为这会导致module耦合，导出为独立library的时候会出问题，也影响多module build的速度。

- task




settings.gradle  定义需要包含哪些module

gradle.properties 配置gradle设置

local.properties 配置本地环境，例如SDK所在目录。因为是Android studio自动生成的本地环境信息，所以不能手动更改，也不能提交到版本控制里面。





如何用命令行  build

自定义build配置

- 配置build type

- Product Flavors

- Build Variants


