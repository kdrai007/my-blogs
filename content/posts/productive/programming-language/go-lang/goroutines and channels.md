---
title: "goroutines and channels"
draft: false
---

Tag: #go-lang #channels

# Concurrency in Go

Go's concurrency model is based on the concept of **goroutine, lightweight threads** that can manage functions cuncurrently. On the other hand , Channels is built-in communication mechnism for safe and efficient data exchange between goroutines.

Go's concurrency modles enable developers to write program that can: 

- Handle multiple programs simultenously 
- Utilize multi-core processor efficiently
- Write concurrent code that is safe, and easy to maintain.


## Go-Routines and channels

A goroutine is a lightweight thread manage by go runtime.It is a function that run on go runtime. 

Goroutine allow you to start up and run another thread of execution concurrently within your program.

Channels are used to communicate between goroutines. It is typed conduit through which you can send and receive vales fromt the channel operator. `<-`

- implementation of goroutine

```go
package main

import (
	"time"
	"fmt"
)

func sendMessage(msg string){
	time.Sleep(time.Duration(1000)*time.Millisecond)
	fmt.Println(msg)
}

func main(){
	sendMessage("test") //sync

	go sendMessage("test1") //async
	go sendMessage("test2") //async
	go sendMessage("test3") //async

	sendMessage("main")
	time.Sleep(2*time.Second)
}

// Output are random like: 

// test
// test2
// main
// test1
// test3

```

### WeightGroups 

Unlike the `time.Sleep(2*time.Second)` used in the example above , the `WeightGroups` are more standard to wait for goroutines to finish executing.

It is simple way to synchronize multiple goroutines.


```go
package main

import (
	"time"
	"fmt"
	"sync"
	"math/rand"
)

func sleep(){
	time.Sleep(time.Duration(rand.Intn(1000))*time.Millisecond)
}
func sendMessage(msg string, wg *sync.WeightGroup){
	defer wg.Done() // run at end of function
	sleep()

	fmt.Println(msg)
}

func main(){
	var wg sync.WeightGroup

	wg.Add(5)
	sendMessage("test",wg) //sync

	go sendMessage("test1",wg) //async
	go sendMessage("test2",wg) //async
	go sendMessage("test3",wg) //async

	sendMessage("main",wg)

	wg.Wait()
}

// Output will be random

```
**Channels**

In their simplest form,one goroutine writes messgaes to channels and another goroutines receives the messages out channels.

example,

```go
package main

func main(){
	msgChan:=make(chan string) // make is used to create channels 

	// Write message into channel
	msgChan <- "hello! world"

	// Read message out of channel
	msg:=<-msgChan
}
```
Above example, create channel `msgChan` of type	`string`


#### Implementation of channels with goroutine

```go
package main

import ( "fmt"
	"time"
	"math/rand"
)

func main(){
	msgChan:=make(chan string)
	go func(){
		time.Sleep(time.Duration(rand.Intn(1000))*time.Millisecond)
		
		msgChan <- "hello world"
		msgChan <- "hello world 2"
	}

	msg1:= <-msgChan
	msg2:= <-msgChan

	fmt.Println(msg1,msg2)
}
```

- Channels behave as *first in first out* queue 

### Channel Buffers

Channels can be `buffered` and `Unbuffered`. Previous examples are of unbuffered channel.

**Unbuffered Channel:** An unbuffered channel causes the sender to block immediatly after send a message into the channel until the receiver receive the message. 

**Buffered Channel:** A buffered channel allow users to send messages to channel until the buffer is full. 

example, 

`msgChan:=make(chan string, 2)`

now `msgChan` can only hold upto 2 messages


#### Channel Directions

When using channels as function parameters , by default you can send and receive message within the function. To provide additional safety at compile time, channel function can be defined as `read-only` or `write-only` 

example,

```go
package main

func reader(bufChan <-chan string){
	msg:=<-bufChan
}

func writer (bufChan chan<- string,msg strring){
	bufChan <- msg
}
```
So, in above example reader function have `read-only` channel direction and writer function have `write-only` channel direction.


#### Handle multiple channel communication with Select

The `select` statement lets a goroutine wait on multiple communications operation.A `select`  satement wait while one executues, it execute randomly in case multiple case are ready. 

example, 

```go
package main

// define some functions here for goroutine

func main(){
	chan1:=make(chan string)
	chan2:=make(chan string)

	for {
		select {
		case msg:=<-chan1:
			println(msg)
		case msg:=<-chan2:
			println(msg)
		}
	}
}
```
The example above shows that, selct will print whenever any channel receive the message


