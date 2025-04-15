# log-plus -- simple async log library
简单异步日志库，基于log库

---
#### 项目地址

###### 特性
* 基于官方log库实现，切换容易
* 支持分类设置日志级别
* 终端使用 ansi color 输出日志
* 支持同步与异步日志方式
* 异步日志可选线程模式及tokio的协程模式
* 支持输出到控制台与文件
* 日志文件支持设置最大长度


###### 第三方依赖
* log
* parking_lot
* crossbeam
* time [optional]
* chrono [optional]

---
###### 添加依赖
`cargo add log-plus`
###### 使用
```rust
use log_plus;
use log;

fn main() {
	let log_level = log_plus::parse_level("debug").unwrap();
	let log_max = log_plus::parse_size("100k").unwrap();

	log_plus::Builder::new()
		.level_str("debug").unwrap()
		.log_file("app.log".to_string())
		.log_file_max_str("100k").unwrap()
		.use_console(true)
		.use_async(true)
		.builder().unwrap();

	log::trace!("hello {}!", "trace");
	log::debug!("hello {}!", "debug");
	log::info!("hello {}!", "info");
	log::error!("hello {}!", "error");
}
```
