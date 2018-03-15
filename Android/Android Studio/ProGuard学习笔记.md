# ProGuard学习笔记


## Proguard的作用

1、压缩代码，移除未使用的类、字段、方法和属性
2、优化字节码，移除未使用的代码指令
3、混淆

## Proguard的使用

### 启用Proguard

	android {
    	buildTypes {
        	release {
        	    minifyEnabled true
        	    proguardFiles getDefaultProguardFile('proguard-android.txt'),
        	            'proguard-rules.pro'
        	}
    	}
	    productFlavors {
        	flavor1 {
        	}
        	flavor2 {
            	proguardFile 'flavor2-rules.pro'
        }
    }
    	...
	}

- minifyEnabled true：启用Proguard，因为会拖慢build的速度，所以最好在release的时候使用，debug不要打开。
- proguardFiles：定义Proguard规则
	- getDefaultProguardFile('proguard-android.txt')：从 Android SDK tools/proguard/ 文件夹获取默认的 ProGuard 设置。使用 proguard-android-optimize.txt 文件可以进一步压缩代码，减小APK大小提高运行速度。
	- proguard-rules.pro：用于添加自定义 ProGuard 规则。

- productFlavors：多渠道打包可以根据需要添加Proguard规则


### 自定义要保留的代码

