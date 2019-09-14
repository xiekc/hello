# Service Computing 实验报告

16327109 谢昆成

## 实验要求

仔细阅读 官方文档 [如何使用Go编程](https://go-zh.org/doc/code.html) ，并按文档写第一个包，做第一次测试。

## 实验内容

### Go语言环境的安装

大家如果不知如何安装Go语言环境，可以参考这篇文章[Go语言环境安装](https://www.runoob.com/go/go-environment.html)。

### VSCode安装GO语言依赖工具

因为无法直接访问相关网址，所以VSCode安装Go的依赖工具总会出现问题。可以参考笔者的[Go 无法安装远程包的问题](https://blog.csdn.net/xiekch/article/details/83036815))来解决这个问题。

### Go包

每个 Go 程序都是由包构成的。程序从 `main` 包开始运行。

就像Java一样，Go需要在开头说明package。除main外，其他包路径都是和文件路径统一的。

### 编写stringutil包

创建目录`$ mkdir $GOPATH/src/github.com/xiekc/stringutil`，在该目录下创建名为`reverse.go`的文件。（xiekc为本人github的username，可替换为自己github的username）

按照 [如何使用Go编程](https://go-zh.org/doc/code.html) 编写好包的内容。可用`go build`测试语法等是否正确。

通过` go install github.com/xiekc/hello`安装hello程序，在这过程中`go` 工具都会安装它所依赖的任何东西如`stringutil`。再运行`hello`，便可得到正确结果`Hello, Go!`。

### 测试

 Go拥有一个轻量级的测试框架，它由 `go test` 命令和 `testing` 包构成。 

用于测试的代码文件必须以`_test.go`作为后缀，包含名为 `TestXXX` 且签名为 `func (t *testing.T)` 函数。测试文件放在同一包中。 测试框架会运行每一个这样的函数；若该函数调用了像 `t.Error` 或 `t.Fail` 这样表示失败的函数，此测试即表示失败。 

编写好`reverse_test.go`后，进入包目录，运行`go test`。若输出`ok`， 则说明通过测试。

### 远程包

`go`工具可通过导入路径的描述从远程代码库自动获取包的源代码。

我们通过把编写好的本地代码推送到github的responsibility上，就可以使用`go get` 就会自动地获取、
构建并安装它。他人就可以使用我们的包了。

所以遵循使用同样的导入路径的约定可让他人以最简单的方式使用你的Go包。