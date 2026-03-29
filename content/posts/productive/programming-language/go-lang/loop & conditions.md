---
title: "loop & conditions"
draft: false
---

Tag : #programming #for_loop #Go 
# Loop & Conditions
## Loop

Go has only one way to make loops. it's called `for` loop

- Basic for loop has 3 components seperated by semicolon `;`
	- The init statement : executed before the first iteration
	- the condition expression : evaluation before iteration
	- the post statement : executed after the iteration 

syntax,
`for i :=0;i<10;i++{//expression}`

```go
package main
import "fmt"

func main(){
sum := 0
for i:=0;i<10;i++{
	sum+=i;
	}
fmt.Println(sum)
}
```
`output: 45`

- The init and post statements are optional.

```go
sum:=1
for ;sum<1000;{
sum+=sum;
}
fmt.Println(sum)
```
`output:1024`

### For is Go's while

At that point you can drop the semicolons: C's `while` spelled `for` in go

syntax,

`for sum<1000{sum+=sum}`

> If you omit the loop condition it loops forever, so an infinite loop is compactly expressed.

syntax,

`for {}`

## conditions

### If

Go's `if` statements are like its `for` loops, the expression need not be surrounded by the parentheses () but the braces { } are required

```go
import "fmt"

func main(){
sum:=10
if sum>10{
	fmt.Println("sum is more than 10")
	}

}
```

#### If with the short statement

Like, `for`, the `if` statement can start with a short conditon to execute before the condition 

- variable decleared by the statement are only in scope until the end of the `if`

syntax,
```go
import (
"fmt"
"math"
)

func powerOf(x,y,limit int) int{
if v:=math.Pow(x.y);v<limit
	{
		return v
	}
return limit
}

func main(){
fmt.Println(
	powerOf(2,4,10),
	powerOf(2,2,20)
	)
}
```
`output: 10 4`




