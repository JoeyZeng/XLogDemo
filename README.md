# XLogDemo
For iOS to use Mars/XLog 

## 背景
XLog是安全高效的日志系统，跨平台。本仓库只是针对iOS的使用案例，鉴于一些不会入门Mars，根据官方文档还不知道怎么接入的新手朋友参考。
https://github.com/Tencent/mars/wiki/Mars-iOS%EF%BC%8FOS-X-%E6%8E%A5%E5%85%A5%E6%8C%87%E5%8D%97

## 介绍
1、使用的是Mars-1.3版本，针对Xlog编译出支持BitCode、模拟器、真机都适用的framework版本。
```
# file /Users/zengzhaoying/Documents/MyCode/XLogDemo/XLogDemo/XLog/mars.framework/mars 
/Users/zengzhaoying/Documents/MyCode/XLogDemo/XLogDemo/XLog/mars.framework/mars: Mach-O universal binary with 3 architectures: [arm_v7:current ar archive] [x86_64] [arm64]
/Users/zengzhaoying/Documents/MyCode/XLogDemo/XLogDemo/XLog/mars.framework/mars (for architecture armv7):	current ar archive
/Users/zengzhaoying/Documents/MyCode/XLogDemo/XLogDemo/XLog/mars.framework/mars (for architecture x86_64):	current ar archive
/Users/zengzhaoying/Documents/MyCode/XLogDemo/XLogDemo/XLog/mars.framework/mars (for architecture arm64):	current ar archive
```
2、在官方Demo基础上，简单封装工具类
```
/// 初始化Log，一般放在main()，要在所有写日志方法前面
/// @param enableConsole 同步到控制台日志输出，比较影响性能，default is NO
/// @param logLevel 推荐Debug使用kLevelDebug，release用kLevelInfo
/// @param logPath 存放路径，默认是在Document/XLog/
/// @param logFilePre 默认Log_20220219.xlog，定义log文件前缀
/// @param maxFileSize 默认同一天Log存放在一个文件，限制最大文件大小，建议是5M
/// @param maxAliveDuration 单位秒，默认10天
/// @param encodePubKey 加密再存储，必要时才传
+ (void)logInitialize:(BOOL)enableConsole
             logLevel:(TLogLevel)logLevel
              logPath:(nullable NSString *)logPath
           logFilePre:(nullable NSString *)logFilePre
          maxFileSize:(nullable NSNumber *)maxFileSize
     maxAliveDuration:(nullable NSNumber *)maxAliveDuration encodePubKey:(nullable NSString *)encodePubKey;
```
