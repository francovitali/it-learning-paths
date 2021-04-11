# Golang

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


