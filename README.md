修改备注 
=====
基于修改的spdlog版本：20170615 master 版本

---
主要修改三个文件：
1、spdlog.h 文件
2、sinks\file_sinks.h 文件
3、details\spdlog_impl.h 文件

修改文件的原始文件在changed目录下。

---
修改了rotating_logger_mt模式：

1、日志文件大于指定的大小会重新创建日志；

2、每天0点0分也会重新创建日志文件；

3、日志名字格式：name_进程号_2017-05-11-133200.log

使用说明
=====
```
auto rotating_logger = spd::rotating_logger_mt("some_logger_name","PtSvr",1024*10);
for(auto i = 0;i < 10;i++){
	rotating_logger->info("Some log message");
}

/*运行时调整全局日志输出等级*/
spd::set_level(spd::level::info); //Set global log level to info

/*调整日志输出格式*/
spd::set_pattern("*** [%H:%M:%S %z] [thread %t] %v ***");
```