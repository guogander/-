

# 开发配置管理通用库解决方案 #

## 目录

###  基础功能  ##
- 加载和解析 JSON、YAML 格式配置文件
- 设置默认配置值
- 完善的使用文档
### 可选功能 ##
- 支持使用弃用配置项时，输出告警信息
- 支持从 Shell 环境变量读取配置项
- 支持从命令行参数读取配置项

### 使用

- 如何加载（初始化）配置(将数据写入配置文件)
- 如何注册配置项（配置组）
- 如何获取配置项的值

##  基础功能

## 1、加载和解析 JSON、YAML 格式配置文件

### （1）加载json配置文件

例：config.json文件如下

```json
{
  "redis": "127.0.0.1:33000",
  "mysql": {
    "port": 3306,
    "host": "127.0.0.1",
    "username": "root",
    "password": "123456"
  }
}
```

代码解析：

```go
package main

import (
	"fmt"

	"github.com/spf13/viper"
)

type Config struct {
	Redis string
	MySQL MySQLConfig
}

type MySQLConfig struct {
	Port     int
	Host     string
	Username string
	Password string
}

func main() {
	// 读取 json 配置文件
	var config Config
	vjson := viper.New()
	vjson.SetConfigName("config")
	vjson.SetConfigType("json")
	vjson.AddConfigPath(".")

	if err := vjson.ReadInConfig(); err != nil {
		fmt.Println(err)
		return
	}

	vjson.Unmarshal(&config)
	fmt.Println("read config.json")
	fmt.Println("config: ", config, "redis: ", config.Redis)
}
```

输出如下:

```
read config.json
config:  {127.0.0.1:33000 {3306 127.0.0.1 root 123456}} redis:  127.0.0.1:33000
```



### （2）加载yaml配置文件



## 2、设置默认配置值


# TFGo配置管理包

构建管理通用包。

## 背景描述（Background）

公司最近几个月开始采用 Go 编程语言技术栈，有一些通用的功能是很多项目都需要的。为了保证项目技术栈的统一，减少重复代码，所以需要构建通用包。

## 方案描述（Solution Description）

描述采取什么样的方案去解决问题。

## 方案特点（Solution Features）

描述方案的特点。

## 使用场景（Use Cases）

描述方案的使用场景。

## 竞品分析（Alternatives）

描述其他方案。

## 参考资料（References）

> <a href="https://www.cnblogs.com/jiujuan/p/13799976.html#2615415638">九卷-viper使用</a>

```go
package main
import "fmt"

func main(){
    fmt.Println("这是一个代码块")
}
```

