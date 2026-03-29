---
title: "generics"
draft: false
---

### Generic Types

Tags: #javascript #typescript #type-definitions

The type of generic functions are just like those of non-generic functions, with the type parameters listed first, similarly to functions declarations: 

- Generics are defined using `<T>` angle brackets, here `T` is just for example.

```ts
function identity<Type>(arg:Type):Type{
	return arg;
}
```

We can also write the generic types as a call signature for an object literal types:-

```ts
function identity<Type>(arg:Type):Type{
	return arg;
}

const myIdentity:{<Type>(arg:Type):Type}= identity;

```

For ex, suppose if you want to create a function and define its type, we can do it this way:-

```ts
const arrType=<T,U>(arr:T[],fn:(val:T)=>U)=>arr.map(fn)
// Here, this arrType function take two argument ("arr,fn" with their names they are self-explanatory) 
// Generally, it's little complex for beginners to define types of these type of function.
```

#### Generic Class

A generic class has a similar shape to a generic interface. Generic class have a generic type parameter list in angle brackets `<>` following the name of the class.

```ts
class GenericClass<Type>{
	value:<Type>
	print:(x:Type,y:Type)=>void;
}
// This is basic class used for an example, it does nothing but take a value then print the value.

const genericClass= new GenericClass<string>();
genericClass.value="";
genericClass.print=("a","b")=>console.log(a,b)
```

This is pretty literal use of generics in `GenericClass` class , but as you can see nothing is restricting this class to only use `string` as a value. We can use `number` or any complex object.

- Static members can't use the class's generic type parameters.

#### Generic type Constraints

Generic constraint are way to **limit the types** that can be used with generic type parameter.

```ts
function printLength<Type>(arg:Type):T{
	console.log(arg.length) // 💥 Error: 'length' does not exist on type `Type`
	return arg;
}
```

Typescript throws error because it doesn't know that every possible type `T`(number, boolean, or custom object) contains a 'length' property. It's too generic!.To consolidate this error, we can use generic constraints to fix this by guaranteeing that the type argument will have properties you need.

```ts
interface Length{
	lenght:number;
}

function printLength<Type extends Length>(arg:Type):T{
	console.log(arg.length) 
	return arg;
}

```

By using `extends` keyword in the generic declaration `<T extends Length>` . In simple terms we have make sure every parameter have `length` type available.


```ts
//           v-----v argument identifier
const drive=(carType:CarType)=>{
//					 ^------^ argument type constraint
// function logic
}

//		   v-----v type parameter identifier
type Drive<CarType> = (carType:CarType)=>{
	// ...
}

```

#### Index Signatures

Index signatures allow you define the shape of objects when you don't know the property name in advance, but do know the type of keys and type of value thye will have.

```ts
interface Object {
	[key:string]:number
}

const myObject:Object={
	history:55,
	math:56,
	"social Science":88
}

// ✅  Works
myObject.english=25

// ❌ Error value must be a number
myOject.grade="A+";
```

- All explicitly declared properties must match the index signature type:-

```ts
interface Object{
	value:string // ❌ error: if you use string index with number values.
	[key:string]:number
}

// To fix

interface Object{
	value:string
	[key:string]:number | string;
}

```

#### Index types

Index types allow users to look inside other types. They are useful tool when accessing Arrays/Tuple values, Object values , and more!

```ts

// For arrays

type Cars=["Bugatti","Ferrari", "Lambo", "Porche"]
type SecondChar=Cars[1]

```

#### Literal Data types

Javascript, like most programming language has concept like **primitive data types**. Primitive data types are `string`, `number` and `boolean`. But typescript provide **literal data types**, you can think of literal data types as being an infinite set of subsets of their primitive counterparts.

```ts
type Days = "Monday" | "Tuesday" | "Wednesday" | "Thrusday" | "Friday" | "Saturday" | "Sunday";

function BreakDay(day:Days){
    if(day==="Sunday")
        console.log("Enjoy! it's break day");
    else 
        console.log("Nope! it's workday");
    
}
```



