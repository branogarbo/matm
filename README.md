# 🔮 **mtrix**
**A tool for performing basic matrix operations.**

---

## 🧪 **Setup**
Download and compile from sources:
```
go get github.com/branogarbo/mtrix
```
Install just the binary with Go:
```
go install github.com/branogarbo/mtrix@latest
```

Or get the pre-compiled binaries for your platform on the [releases page](https://github.com/branogarbo/mtrix/releases)


## 🧙‍♂️ **CLI Usage**
```
mtrix

A tool for performing basic matrix operations.

Usage:
  mtrix [command]

Available Commands:
  add         Get the sum of two matrices
  det         Compute the determinant of a matrix
  help        Help about any command
  mult        Multiply two matrices together
  smult       Multiply a matrix by a scalar
  sub         Get the difference of two matrices
  trans       Get the transpose of a matrix

Flags:
  -h, --help        help for mtrix
  -r, --raw-input   Whether or not the command takes matrices as strings

Use "mtrix [command] --help" for more information about a command.
```

---

## 🌌 **Package Usage**
Get the packages you need for your project:
```
go get github.com/branogarbo/mtrix/add
go get github.com/branogarbo/mtrix/mult
go get github.com/branogarbo/mtrix/util
...
```

### **Examples:**
Adding two matrices and printing the result:
``` go
package main

import (
	"fmt"
	"log"

	"github.com/branogarbo/mtrix/add"
	"github.com/branogarbo/mtrix/util"
)

func main() {
	mat1 := util.Matrix{
		RowsNum: 3,
		ColsNum: 3,
		Value: util.MatVal{
			{1, -4, 9},
			{2.7, 3, 7},
			{0, -3.3, 8},
		},
	}

	mat2 := util.Matrix{
		RowsNum: 3,
		ColsNum: 3,
		Value: util.MatVal{
			{1, 1, 1},
			{1, 1, 1},
			{1, 1, 1},
		},
	}

	resultMat, err := add.MatAdd(mat1, mat2)
	if err != nil {
		log.Fatal(err)
	}

	util.PrintMat(resultMat)
}
```

Multiplying two matrices together and printing the result:
``` go
package main

import (
	"log"

	"github.com/branogarbo/mtrix/mult"
	"github.com/branogarbo/mtrix/util"
)

func main() {
	mat1 := util.Matrix{
		RowsNum: 3,
		ColsNum: 2,
		Value: util.MatVal{
			{1, -4},
			{2.7, 3},
			{0, -3.3},
		},
	}

	mat2 := util.Matrix{
		RowsNum: 2,
		ColsNum: 2,
		Value: util.MatVal{
			{1, 0},
			{0, 1},
		},
	}

	resultMat, err := mult.MatMult(mat1, mat2)
	if err != nil {
		log.Fatal(err)
	}

	util.PrintMat(resultMat)
}
```