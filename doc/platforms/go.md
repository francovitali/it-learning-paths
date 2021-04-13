# Go

## Installation

1. Download (https://golang.org/dl/)
2. Install Go [extension](https://marketplace.visualstudio.com/items?itemName=golang.Go) on [Visual Studio Code](https://code.visualstudio.com/)

## Reference

* [Getting Started Tutorial](https://golang.org/doc/tutorial/getting-started)

## Package Managers

### Workspace

> As of Go v1.13, $GOPATH mechanics is now largely irrelevant (by default on 1.14+)

### Go Modules ([reference](https://www.honeybadger.io/blog/golang-go-package-management/))

Go Modules are now supported by the platforms as the official package manager

* **go mod init**: will initialize modules in your project.
* **go get**: adds a new dependency, and you can use go get -u or go get -u=patch to upgrade a dependency to a new minor or patch version.
* **go mod tidy**: cleans up unused dependencies or adds missing dependencies.
* **go mod vendor**: copies all third-party dependencies to a vendor folder in your project root.

> The files **go.mod** y **go.sum** must be commited to source control

## Let's make our first application!

We're going to create a simple api

1. First, we create an empty folder with our project name "my-go-api"

```bash
$ mdkir -p ~/src/github.com/francovitali/my-go-api
cd ~/src/github.com/francovitali/my-go-api
```

2. Initialize the project folder as a git repo

```bash
$ git init
```

3. Initialize the project as a Go Module

```bash
$ go mod init github.com/francovitali/my-go-api
```

4. Import module dependencies

```bash
$ go get -u github.com/gin-gonic/gin
$ go get -u github.com/go-redis/redis
$ go get -u github.com/go-sql-driver/mysql
```

5. Add project files



