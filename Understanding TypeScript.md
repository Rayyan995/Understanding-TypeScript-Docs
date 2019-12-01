# Understanding TypeScript

1. [Instal](#install)
2. [Data Types](#Data_Types)
3. [TypeScrypt Compiler](#TypeScrypt_Compiler)
4. [Next Gen JS and TS](#Next_Gen_JS_and_TS)
5. [Classes & Interfaces](#Classes_&_interfaces)

<br>

# install

``` cli
npm i -g typescrypt
```

# Data_Types 

## number 

used for all types of numbers as integer, float, or even negative and positive.

**Note:** if we initialize a value to the a variable during the declaration we can not assign that variable with a different type as:

``` ts
let bum = 5;
num = "text";
```

initializing a variable with a number give it the type of the initial value and this call **Type reference**

the ` ` num = "text" ` ` will produce an error assigning the variable to a different data type.

In TypeScript we **not** access a not existing property ex:

``` ts
const person = {
    name: "Rayyan",
    age: 24,
    hobbies: 
}
console.log(date.number); // with will produce an error that number is not a property in person object
```

## Arrays

 Can have a type array and a type data that array will take:

``` ts
const arr = ["he", "good"];
```

this array can not take any non-string data 

## Tuple

is a fixed-size array and fixed-data types of the array value ex:

``` ts
tuple = [24, "rayyan"]; // it always has two elements, the first is number and the second is string
```

## Enum

 is a custom data type and take the same behavior in C language ex:

``` ts
enum Role {ADMIN, USER, READ_ONLY}
if(Role.ADMIN) // ADMIN take value of zero and the next incremented by one and so on
```

## Literal types

a variable can take a specific values of a specific types es:

``` ts
resultTypes: "as-number" | "as-string" | 0 | 1
```

so resultTypes will produce an error if we try to assign it with a different value

## Type Aliases / Type Custom / Union

is defined using `type` key word ex:

```ts 
type combine = number | string; 
type accepted values = "as-number" | "as-string"

``` 

## any and unknown 

a variable of any can be assigned to all other types such as number or string, ..., ex:

```ts
let generalVar: any;
generalVar = "text"
generalVar = 10

let text: string;
text = generalVar;
let num: string;
num = generalVar
```

but using **unknown** type instead of **any** will produce an error of mis type

## never

it's data type for functions and when the function has a return type of **never** so it does not return anything it even does not return **undefined** the corresponding to `void` as a return type.

# TypeScrypt_Compiler

## compile a file

hit the command

``` cli
tsc <file name>
```

To make the file automatic compile after any change in the code add `--watch` or `-w` and this called **watch** mode tp the command, so"

``` cli
tsc -w <file name>
```

## compile the entire project

Hit the next two commands in the project directory

``` cli
tsc --init
```

``` cli
tsc 
```

Or for automatic reload for any change

``` cli
tsc -w
```

## Exclude and Include files

we exclude some file from compilation process by adding exclude : [...] property in the *tsconfig.json* and this array have all the files the directories that i do not want to compile them.

In opposite to that is using `include` property to include only the files we want to compile, we can use `files` instead of `include` to specify files only without directories.

## lib property

Used to specify some libraries that used in the project as **dom**, when we write the code to run on the browser

## sourceMap property

make it equal to true allow browser to view the source code of TypeScrypt in debugger tools.

## outDir

tell the compiler where to save the compile output (JS files), ex:

``` json
"outDir": "./dist"
```

## rootDir

tell the **compiler** to look at a specific folder as the root so it compile only this folder, ex:

``` json
"rootDir": "./src"
```

## noEmitOnError

 tell the compiler not to produce output files(JS files) if there is ab error in **TypeScrypt** files, ex:

``` json
"noEmitOnError": true,
```

# Next_Gen_JS_and_TS

Nothing to add, almost everything are already known

# Classes_&_interfaces

## Private & Protected

`private` make property can not be used outside the class even **child** class can not use private properties of **parent** class, but `protected` makes property can not be used outside the class and in the time time can be used in child class.

## setters and getters (Encapsulation)

we use setters to set a value to a class property specially if that property is private, so by using them we access private properties and that called **Encapsulation**

And getters works in the same behavior of setters but it's used to retrieve a value of a class property specially when it  is private.

In the below example we use `set` and `get` keywords to define them:

``` ts
class ITDepartment {
    private lastReport: string;
    constructor(report: string) {
        this.lastReport = report;
    }

    get getLastReport() {
        return this.lastReport
    }

    set setLastReport(report: string) {
        this.lastReport = report
    }
}

const ITDepartment_1 = new ITDepartment("Report___from_Rayyan");

console.log(ITDepartment_1.getLastReport) // notice we don not call them as method but as a normal class property 
ITDepartment_1.setLastReport = "Report___from_Anne" // We call them as method but as a normal class property 
```


## Singleton && private constructor

when we enforce a class to just have one instance that is called **Singleton Pattern**, we do that the help of defining the **constructor** as private using `private` keyword, in the below example *ITDep_1* and *ITDept* are the same instance of the class *ITDepartment*:

```ts
class ITDepartment {
    private static instance: ITDepartment;
    private lastReport: string;
    private constructor(id: string, report: string) {
        this.lastReport = report;
    }
    static getInstance() {
        if (this.instance) {
            return this.instance
        }
        this.instance = new ITDepartment("IT", "______")
    }
}
const ITDep_1 = ITDepartment.getInstance();
const ITDep_2 = ITDepartment.getInstance();
console.log(ITDep_1);
console.log(ITDep_2);
```



