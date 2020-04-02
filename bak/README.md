# gomodules1

https://medium.com/@adiach3nko/package-management-with-go-modules-the-pragmatic-guide-c831b4eaaf31  

###  Initialize the module as a git repo
NOTE: Alternatively, as a local module you can do go mod init gomodules1 - which will have home as current folder
go mod init github.com/coderdba-coding-org/gomodules1

###  Get modules that we think we need
go get github.com/coderdba-coding-org/golang2@master  

\$ go get github.com/coderdba-coding-org/golang2@master
go: finding github.com/coderdba-coding-org/golang2 master
go: downloading github.com/coderdba-coding-org/golang2 v0.0.0-20200401113918-70d295e46e88
go: extracting github.com/coderdba-coding-org/golang2 v0.0.0-20200401113918-70d295e46e88
go: finding github.com/coderdba-coding-org/golang2 latest

\$ ls -l
total 24
-rw-r--r--  1 username  DHC\Domain Users   12 Apr  2 10:34 README.md
-rw-------  1 username  DHC\Domain Users  153 Apr  2 10:38 go.mod
-rw-------  1 username  DHC\Domain Users  251 Apr  2 10:38 go.sum

\$ cd ~/go
\$ find . -name golang2 -print
./pkg/mod/cache/download/github.com/coderdba-coding-org/golang2

\$ cat go.sum
github.com/coderdba-coding-org/golang2 v0.0.0-20200401113918-70d295e46e88 h1:+OrIH2t7XZuijpIXYrC0LHIgfrlutCsn4nsZzvEGIyc=
github.com/coderdba-coding-org/golang2 v0.0.0-20200401113918-70d295e46e88/go.mod h1:fb766f985rySthNMhkRqedQgqEiAW7o6j4Kr3JBrTzs=

$ cat go.mod
NOTE: The 'indirect' flag is because no code of this repo is using that pulled module
module github.com/coderdba-coding-org/gomodules1

go 1.12

require github.com/coderdba-coding-org/golang2 v0.0.0-20200401113918-70d295e46e88 // indirect

###  Tidy up unused pulled modules
$ cp go.mod go.mod.bak
$ go mod tidy
NOTE: Depending on the current state of your repo, this will either prune the unused module or remove // indirect comment.

$ cat go.mod
module github.com/coderdba-coding-org/gomodules1

go 1.12

### Note on go-get
Commands like go build or go test will automatically download all the missing dependencies though you can do this explicitly with go mod download to pre-fill local caches which may prove useful in CI.
By default all our packages from all projects are downloaded into $GOPATH/pkg/mod directory. 


### List
$ go list
go: finding github.com/coderdba-coding-org/golang2 latest
build github.com/coderdba-coding-org/gomodules1: cannot load github.com/coderdba-coding-org/golang2: cannot find module providing package github.com/coderdba-coding-org/golang2

$ go list -m all
github.com/coderdba-coding-org/gomodules1
github.com/coderdba-coding-org/golang2 v0.0.0-20200401113918-70d295e46e88


