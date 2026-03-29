---
title: "variables"
draft: false
---

# Go - Variables

Tag : #Go #go_lang #programming

The `var` statement declears list of variables

- As in function argument list,the type is last
- A `var` statement can be at package or function level, we can see both in given example

syntax,

```go
package main
import "fmt"
var c,python,java bool

func main(){
var i int
fmt.Println(c,python,java,i)
}
```
`output: false false false 0`


## Variables with initializers

A var declearation can include initlializers, one per variable

- If an initlializers is present, the type can be omitted; the variable will take type of the initliazers

syntax,

```go
var i,j int = 1,2

func main(){
var c,python,java = bool,bool,"no!"
fmt.Println(i,j,c,python,java)
}
```
`output: 1 2 false false no!`

## Short Variables declearations

Inside a function, the `:=` short assignment statement can be used in place of `var` declaration with implicit type

- Outside the function, every statement start with the keyword (var,func and so on) and so the `:=` construct is not available

syntax,

```go
var i,j int = 1,2

func main(){
c,python,java := bool,bool,"no!"
fmt.Println(i,j,c,python,java)
}
```
`output: 1 2 false false no!`

### Basic Variables types

Go,s basic types are:

```go
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

- The `int` ,`uint` and `uintptr` typers are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit systems
- If you need to use integer just use `int` unless you have reason to use sized or unsigned int type.

syntax,

```go
var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)

func main() {
	fmt.Printf("Type: %T Value: %v\n", ToBe, ToBe)
	fmt.Printf("Type: %T Value: %v\n", MaxInt, MaxInt)
	fmt.Printf("Type: %T Value: %v\n", z, z)
}
```
`output:`
`Type: bool Value: false`
`Type: uint64 Value: 18446744073709551615`
`Type: complex128 Value: (2+3i)`


#### Default values or Zero values

Variables declared without an explicit initial value are given theri `zero` value.

- The Zero value is:
	- 0 for numeric types
	- false for boolean types
	- ""(the empty string) for strings
	
syntax,

```go
func main() {
	var i int
	var f float64
	var b bool
	var s string
	fmt.Printf("%v %v %v %q\n", i, f, b, s)
}
```
`output: 0 0 false ""`


### Type Conversions

The expression `T(v)` converts the value `v` to type `T`

```go
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)

// or simply write this

i :=42
f := float64(i) // here i converts to float64 and assigned to f
u := uint(f)
```

- Unlike in C, in Go assignment between items of different type requires an explicit conversion.

### Type inference

When declearing a variable without specifying an explicit type (either by using the `:=` or `var=` expression syntax) the variable's  type is inferred from the value of right hand side.

`var i=32 //type int`
`var i=32.00 //type float64`
`var i="heythere" //type string`

### Constants

Constants are decleared like variables, but with the `const` keyword
- Constants can be character,string,boolean or numeric values
- Constants can't be decleared using `:=` syntax.

```go
import "fmt"

const Pi = 3.14

func main() {
	const World = "世界"
	fmt.Println("Hello", World)
	fmt.Println("Happy", Pi, "Day")

	const Truth = true
	fmt.Println("Go rules?", Truth)
}
```

#### Numeric Constants

Numeric constants are high-precision values
- An untyped constant takes the type needed by its context.

```go

const (
	// Create a huge number by shifting a 1 bit left 100 places.
	// In other words, the binary number that is 1 followed by 100 zeroes.
	Big = 1 << 100
	// Shift it right again 99 places, so we end up with 1<<1, or 2.
	Small = Big >> 99
)

func needInt(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
	return x * 0.1
}

func main() {
	fmt.Println(needInt(Small))
	fmt.Println(needFloat(Small))
	fmt.Println(needFloat(Big))
	//fmt.Println(needInt(Big)) through an error
}
```
`output:21`
`0.2`
`1.2676506002282295e+29`

> An `int` can store at maximum a 64-bit integer, and sometimes less.


