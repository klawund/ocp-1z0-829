# Building blocks

## Understanding package declarations and imports

### Important javac options

| Option | Description |
| - | - |
| -cp -classpath --class-path | Location of classes needed to compile the program |
| -d | Directory in which to place the generated class files |

### Important java options

| Option | Description |
| - | - |
| -cp -classpath --class-path | Location of classes needed to run the program |

### Important JAR options

| Option | Description |
| ------ | ----------- |
| -c --create | Creates a new JAR file|
| -v --verbose | Prints details |
| -f --filename | JAR filename |
| -cvf | Create + verbose + filename |

## Creating objects

### Following the order of initialization

- Fields and instance initializers are run in the order they appear in the file
- Constructor runs after all fields and instance initializer blocks have run

```java
public class Animal
{
    public Animal()
    {
        name = "cow";
    }

    String name = "dog";

    {
        name = "sheep";
    }

    public static void main(String[] args)
    {
        Animal a = new Animal();
        System.out.println(a); // cow
    }
}
```

## Understanding data types

### Defining text blocks

- Text blocks must start with a line break.
- \ prevents a line break inside a text block

## Declaring variables

### Identifying identifiers

- Identifiers must begin with a letter, a currency symbol or a _ symbol
- Identifiers can include numbers but not start with them
- A single underscore is not allowed as an identifier
- Java keyworks can not be used as identifiers

## Initiliazing variables

### Inferring the type with var

var applies local variable type inference an as the name states can only be used to automatically infer the type of locally declared variables.

### Type inference with var

When you type var the compiler is instructed to infer the type of the variable based on the type of the value being assigned to it.

Type-inferred declarations are still statically typed which means that the use of var doens't allow a variable to change it's type at runtime.

### Examples with var

```java
var question; // does not compile
var question = null; // does not compile
int a, var b = 1; //  does not compile
```

var is not a reserved keyword, meaning that it can be used to name classes, packages, enums, methods and even variables.

This compiles:

```java
package var;

public class Var
{
    public void var()
    {
        var var = "var";
    }

    public void Var()
    {
        Var var = new Var();
    }
}
```

Refer to [Local variable type inference style guide](https://openjdk.java.net/projects/amber/LVTIstyle.html) for approppriate use cases.

## Managing variable scope

### Understanding garbage collection

Java includes a built-in method to help support garbage collection where you can suggest that garbage collection run:

```java
System.gc();
```

Java is free to ignore you, this method is not guaranteed to do anything.
