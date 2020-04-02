# gomodules1
  
https://medium.com/@adiach3nko/package-management-with-go-modules-the-pragmatic-guide-c831b4eaaf31

###  Initialize the module as a git repo
NOTE: Alternatively, as a local module you can do go mod init gomodules1 - which will have home as current folder
\$ go mod init github.com/coderdba-coding-org/gomodules1

###  Get modules that we think we need
\$ go get github.com/coderdba-coding-org/gojunk@master
go: finding github.com/coderdba-coding-org/gojunk master
go: downloading github.com/coderdba-coding-org/gojunk v0.0.0-20200402072544-6b5e6658f6f0
go: extracting github.com/coderdba-coding-org/gojunk v0.0.0-20200402072544-6b5e6658f6f0

\$ ls -l
-rw-r--r--  1 username  DHC\Domain Users  653 Apr  2 12:56 README.md
drwxr-xr-x  7 username  DHC\Domain Users  224 Apr  2 12:56 bak
-rw-------  1 username  DHC\Domain Users  152 Apr  2 12:56 go.mod
-rw-------  1 username  DHC\Domain Users  249 Apr  2 12:56 go.sum

### Find the downloaded module in $GOPATH which is as of now ~/go (the default)
\$ cd ~/go
\$ find . -name gojunk -print
./pkg/mod/cache/download/github.com/coderdba-coding-org/gojunk

\$ cat go.mod

module github.com/coderdba-coding-org/gomodules1

go 1.12

require github.com/coderdba-coding-org/gojunk v0.0.0-20200402072544-6b5e6658f6f0 // indirect


\$ cat go.sum
github.com/coderdba-coding-org/gojunk v0.0.0-20200402072544-6b5e6658f6f0 h1:flZwNkZxVTVRndx+5BudIkTpsoF8CK7cXQh+udBzMmk=
github.com/coderdba-coding-org/gojunk v0.0.0-20200402072544-6b5e6658f6f0/go.mod h1:7iAJonrssGVS+QkuwAFsbC3Uzxa9Um5eYnUjj0gNzfM=

### Create a program that uses the module gojunk

\$ cat main.go
package main

import (
       "github.com/coderdba-coding-org/gojunk"
)

### Tidy the module file
NOTE: Note that the "//indirect" goes away as we are using the gojunk repo in main.go (or other program in this module)
\$ go mod tidy
\$ cat go.mod
module github.com/coderdba-coding-org/gomodules1

go 1.12

require github.com/coderdba-coding-org/gojunk v0.0.0-20200402072544-6b5e6658f6f0


