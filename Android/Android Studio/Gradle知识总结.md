# Gradle知识总结

## Module的build.gradle分解

	apply plugin: 'com.android.application'  //说明这个build文件中使用Android plugin for Gradle
	//需要用到的plugin
	
	//配置所有针对Android项目build时的选项
	android {
	    compileSdkVersion 19	//编译时用的SDK版本
	    buildToolsVersion "19.0.0"	//build工具的版本
	
		//动态在build时配置AndroidManifest.xml里的项目，可以覆盖manifest里的配置
	    defaultConfig {
	        applicationId "com.example.my.app"
	        minSdkVersion 8
	        targetSdkVersion 19
	        versionCode 1
	        versionName "1.0"
	    }
	    //配置如何构建和打包APP
	    buildTypes {
	        release {
	            minifyEnabled true
	            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
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