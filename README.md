# gofmtdemo

This repo is solely meant to demonstrate some differences between `go fmt` and
`gofmt`. Go files here are deliberately ill-formatted.

Demo:

1. Get a copy of this repo: `go get github.com/rhcarvalho/gofmtdemo`  
  You will have this structure in your `GOPATH`:
  ```
  github.com/rhcarvalho/gofmtdemo
  ├── README.md
  ├── doc.go
  ├── foo
  │   └── doc.go
  └── vendor
      └── bar
          └── doc.go
  ```

2. From anywhere, issuing `go fmt github.com/rhcarvalho/gofmtdemo` will change only `gofmtdemo/doc.go`.  
  Use `git reset --hard` to revert back to the initial state.

3. To recurse into subpackages (subdirectories), run `go fmt github.com/rhcarvalho/gofmtdemo/...`.  
  That will change both `gofmtdemo/doc.go` and `gofmtdemo/foo/doc.go`. Note that the vendored `bar` package is left intact.  
  Again, use `git reset --hard` to revert back to the initial state.

4. `gofmt -l` recurses a directory tree indistinctively:
  ```
  $ (cd $GOPATH/src; gofmt -l github.com/rhcarvalho/gofmtdemo)
  github.com/rhcarvalho/gofmtdemo/doc.go
  github.com/rhcarvalho/gofmtdemo/foo/doc.go
  github.com/rhcarvalho/gofmtdemo/vendor/bar/doc.go
  ```
