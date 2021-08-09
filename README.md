# BuglyHotfixDemo
> 把官方的demo进行升级，适配到AGP4.0.0 （classpath 'com.android.tools.build:gradle:4.0.0'）
由于bugly官方文档更新不及时，不清晰，而自己的项目中又使用到了他们的热修复技术，  之前由于一直停留在AGP3.5.3导致项目想使用google的ViewBind（AGP至少3.6.3）一直拖延，  在自己的不断跟踪bugly的官方文档以及一些反馈和自己的反复测试下，终于完成了bugly的完美升级，  一步到位AGP4.0.0,经过测试,已经在自己的项目中可以完美打差量包，所以本着帮助有相似困扰的小伙伴，  自己把官方的demo拷贝下来，在这个基础上进行升级并通过了自己的测试，有兴趣的小伙伴可以直接拉下来，运行体验一下。

## 注意事项：
__1.由于我的设备是Mac M1款，而bugly又没有适配M1的7zip,导致我当时打差量包，一直在这个地方报错，后来通过安装homebrew,并安装7za,把tinker-support.gradle的7zip路径修改为本地的路径才解决。
  window用户或者mac的X86架构的小伙伴可以把下面的这个path变量注释掉__

```
// tinker-support.gradle
tinkerPatch {
.....
sevenZip {
        zipArtifact = "com.tencent.mm:SevenZip:1.1.10"
        // 2021-08-07 由于使用了M1的mac编译，bugly没有将arm版本的7zip发布到jcenter()中，只能使用本机的7zip来最后打压缩差量包apk
        // 非mac M1用户，把这行注释掉。
        path = "/opt/homebrew/bin/7za"
    }
 .....   
    }
 ```   
    
__2.建议不要修改gradle-wrapper中的gradle版本以及工程的gradle文件的AGP4.0.0版本。  确保自己运行没问题的情况下，可以尝试升级AGP试试，经过我的测试，升级到4.2.0的话
   打release包没有问题，但是打差量包的话，报错，错误为：can't find TINKER_ID from the old apk manifest file, it must be set!  有精力的小伙伴可以尝试升级为4.1.0试试，反馈一下。__
