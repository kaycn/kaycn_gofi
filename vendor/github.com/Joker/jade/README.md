# Jade.go - template engine for Go (golang)  
Package jade (github.com/Joker/jade) is a simple and fast template engine implementing Jade/Pug template.  
Jade precompiles templates to Go code or generates html/template.  
Now Jade-lang renamed to [Pug template engine](https://pugjs.org/api/getting-started.html).  

[![GoDoc](https://godoc.org/github.com/Joker/jade?status.svg)](https://godoc.org/github.com/Joker/jade) [![Go Report Card](https://goreportcard.com/badge/github.com/Joker/jade)](https://goreportcard.com/report/github.com/Joker/jade)

## Jade/Pug syntax
example:

```jade
:go:func Index(pageTitle string, youAreUsingJade bool)

mixin for(golang)
    #cmd Precompile jade templates to #{golang} code.

doctype html
html(lang="en")
    head
        title= pageTitle
        script(type='text/javascript').
            if(question){
                answer(40 + 2)
            }
    body
        h1 Jade - template engine
            +for('Go')

        #container.col
            if youAreUsingJade
                p You are amazing
            else
                p Get on it!
            p.
                Jade/Pug is a terse and simple
                templating language with
                a #[strong focus] on performance 
                and powerful features.
```

becomes

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <title>Jade.go</title>
        <script type="text/javascript">
            if(question){
                answer(40 + 2)
            }
        </script>
    </head>
    <body>
        <h1>Jade - template engine
            <div id="cmd">Precompile jade templates to Go code.</div>
        </h1>
        <div id="container" class="col">
            <p>You are amazing</p>
            <p>
                Jade/Pug is a terse and simple
                templating language with
                a <strong>focus</strong> on performance 
                and powerful features.
            </p>
        </div>
    </body>
</html>
```


See [more](https://github.com/Joker/jade/tree/master/testdata/v2) [examples](https://github.com/Joker/jade/tree/master/example).  


## Example usage

```sh
jade -pkg=main -writer hello.jade
```
jade command precompiles hello.jade to hello.jade.go  

`hello.jade`
```
:go:func(arg) word string
doctype 5
html
    body
        p Hello #{word}!
```

`hello.jade.go`
```go
// Code generated by "jade.go"; DO NOT EDIT.
package main

import "io"

const (
    hello__0 = `<!DOCTYPE html><html><body><p>Hello `
    hello__1 = `!</p></body></html>`
)
func tpl_hello(word string, wr io.Writer) {
    buffer := &WriterAsBuffer{wr}
    buffer.WriteString(hello__0)
    WriteEscString(word, buffer)
    buffer.WriteString(hello__1)
}
```

`main.go`
```go
package main
//go:generate jade -pkg=main -writer hello.jade

import "net/http"

func main() {
	http.HandleFunc("/", func(wr http.ResponseWriter, req *http.Request) {
		tpl_hello("jade", wr)
	})
	http.ListenAndServe(":8080", nil)
}
```

Output on localhost:8080 :
```html
<!DOCTYPE html><html><body><p>Hello jade!</p></body></html>
```
  
  
or generate html/template at runtime


```go
package main

import (
    "fmt"
    "github.com/Joker/hpp" // Prettify HTML
    "github.com/Joker/jade"
)

func main() {
    tpl, err := jade.Parse("name_of_tpl", "doctype 5\n html: body: p Hello #{.Word} !")
    if err != nil {
        fmt.Printf("Parse error: %v", err)
        return
    }

    fmt.Printf( "Output:\n\n%s", hpp.PrPrint(tpl) )
}
```

Output:

```html
<!DOCTYPE html>
<html>
    <body>
        <p>Hello {{.Word}} !</p>
    </body>
</html>
```


## Installation

```sh
$ go get github.com/Joker/jade/cmd/jade
```


## Custom filter  :go
This filter is used as helper for command line tool  
(to set imports, function name and parameters).  
Filter may be located at any nesting level.  
When jade used as library :go filter is not needed.  

### Nested filter  :func
```
:go:func
    CustomNameForTemplateFunc(any []int, input string, args map[string]int)

:go:func(name)
    OnlyCustomNameForTemplateFunc

:go:func(args)
    (only string, input float32, args uint)
```

### Nested filter  :import
```
:go:import
    "github.com/Joker/jade"
    github.com/Joker/hpp
```