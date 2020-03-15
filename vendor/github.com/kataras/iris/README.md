<!-- # Iris Web Framework <a href="README_ZH.md"> <img width="20px" src="https://iris-go.com/images/flag-china.svg?v=10" /></a> <a href="README_RU.md"><img width="20px" src="https://iris-go.com/images/flag-russia.svg?v=10" /></a> <a href="README_ID.md"> <img width="20px" src="https://iris-go.com/images/flag-indonesia.svg?v=10" /></a> <a href="README_GR.md"><img width="20px" src="https://iris-go.com/images/flag-greece.svg?v=10" /></a> <a href="README_PT_BR.md"><img width="20px" src="https://iris-go.com/images/flag-pt-br.svg?v=10" /></a> <a href="README_JPN.md"><img width="20px" src="https://iris-go.com/images/flag-japan.svg?v=10" /></a> -->

# Iris <a href="README_ZH.md"><img width="20px" src="https://iris-go.com/images/flag-china.svg?v=10" /></a> <a href="README_GR.md"><img width="20px" src="https://iris-go.com/images/flag-greece.svg?v=10" /></a> <a href="README_ES.md"><img width="20px" src="https://iris-go.com/images/flag-spain.png" /></a> <a href="README_KO.md"><img width="20px" src="https://iris-go.com/images/flag-south-korea.svg" /></a> <a href="README_FA.md"><img width="20px" src="https://iris-go.com/images/flag-iran.svg" /></a>

[![build status](https://img.shields.io/travis/kataras/iris/master.svg?style=for-the-badge)](https://travis-ci.org/kataras/iris) [![report card](https://img.shields.io/badge/report%20card-a%2B-ff3333.svg?style=for-the-badge)](https://goreportcard.com/report/github.com/kataras/iris)<!--[![godocs](https://img.shields.io/badge/go-%20docs-488AC7.svg?style=for-the-badge)](https://godoc.org/github.com/kataras/iris)--> [![view examples](https://img.shields.io/badge/learn%20by-examples-0077b3.svg?style=for-the-badge)](https://github.com/kataras/iris/tree/master/_examples) [![chat](https://img.shields.io/gitter/room/iris_go/community.svg?color=blue&logo=gitter&style=for-the-badge)](https://gitter.im/iris_go/community) [![release](https://img.shields.io/badge/release%20-v11.2-0077b3.svg?style=for-the-badge)](https://github.com/kataras/iris/releases)

Iris is a fast, simple yet fully featured and very efficient web framework for Go. It provides a beautifully expressive and easy to use foundation for your next website or API.

Learn what [others say about Iris](https://iris-go.com/testimonials/) and **star** this github repository.

> Version 11.2 **released!**

[![https://www.facebook.com/iris.framework/posts/3276606095684693](https://iris-go.com/images/iris-112-released.png)](https://www.facebook.com/iris.framework/posts/3276606095684693)

## It's your time to decide

The Go Team released the go modules[...](https://github.com/kataras/iris/issues/1370)

[![](https://api.gh-polls.com/poll/01DP9QJSMZK2FHP9K5CM712CQT/Keep%20the%20same%20import%20path)](https://api.gh-polls.com/poll/01DP9QJSMZK2FHP9K5CM712CQT/Keep%20the%20same%20import%20path/vote)
[![](https://api.gh-polls.com/poll/01DP9QJSMZK2FHP9K5CM712CQT/Add%20version%20suffix)](https://api.gh-polls.com/poll/01DP9QJSMZK2FHP9K5CM712CQT/Add%20version%20suffix/vote)

> Read how [we support you](https://github.com/kataras/iris/wiki/Support).

[![Iris vs .NET Core(C#) vs Node.js (Express)](https://github.com/kataras/iris/raw/master/_benchmarks/benchmarks_graph_22_october_2018_gray.png)](https://github.com/kataras/iris/blob/master/_benchmarks/README.md)

<details>
<summary>Third-party benchmark</summary>

[![](https://github.com/kataras/iris/raw/master/_benchmarks/benchmarks_third_party_source_snapshot_go_23_october_2018.png)](https://github.com/iris-contrib/third-party-benchmarks#full-table)

> Last updated at: 01 March of 2019. Click to the image to view all results. You can run this in your own hardware by following the [steps here](https://github.com/iris-contrib/third-party-benchmarks#usage).

</details>

## Learning Iris

<details>
<summary>Quick start</summary>

```sh
# assume the following code in example.go file
$ cat example.go
```

```go
package main

import "github.com/kataras/iris"

func main() {
    app := iris.Default()
    app.Get("/ping", func(ctx iris.Context) {
        ctx.JSON(iris.Map{
            "message": "pong",
        })
    })

    app.Run(iris.Addr(":8080"))
}
```

```sh
# run example.go and
# visit http://localhost:8080/ping on browser
$ go run example.go
```

> Routing is powered by [muxie](https://github.com/kataras/muxie), the most powerful and fastest trie-based software written in Go.

</details>

Iris contains extensive and thorough **[wiki](https://github.com/kataras/iris/wiki)** making it easy to get started with the framework.

For a more detailed technical documentation you can head over to our [godocs](https://godoc.org/github.com/kataras/iris). And for executable code you can always visit the [_examples](_examples/) repository's subdirectory.

### Do you like to read while traveling?

<a href="https://bit.ly/iris-request-book"> <img alt="Book cover" src="https://iris-go.com/images/iris-book-cover-sm.jpg" width="200" /> </a>

You can [request](https://bit.ly/iris-request-book) a PDF version and online access of the **E-Book** today and be participated in the development of Iris.


## Contributing

We'd love to see your contribution to the Iris Web Framework! For more information about contributing to the Iris project please check the [CONTRIBUTING.md](CONTRIBUTING.md) file.

[List of all Contributors](https://github.com/kataras/iris/graphs/contributors)

## Security Vulnerabilities

If you discover a security vulnerability within Iris, please send an e-mail to [iris-go@outlook.com](mailto:iris-go@outlook.com). All security vulnerabilities will be promptly addressed.

## License

The project name "Iris" was inspired by the Greek mythology.

Iris Web Framework is free and open-source software licensed under the [3-Clause BSD License](LICENSE).
