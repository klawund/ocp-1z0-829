# Making decisions

## Creating decision-making statements

### Subtypes (pattern matching)

The type of the pattern varible must be a subtype of the variable on the left side of the expression. It also cannot be the same type.

```java
Integer value = 123;
if (value instanceof Integer) {}
if (value instanceof Integer myInt) {} // does not compile
```

### Flow scoping

Flow scoping means the variable is only in scope when the compiler can definitely determine its type. It is defined by the compiler based on the branching and flow of the program.

```java
Number number = 2.0;
if (number instanceof Integer data || date.compareTo(5)) // does not compile
```

When scoped, the variable is not exclusive to the block. This compiles:

```java
void print(Number number)
{
    if (!(number instanceof Integer data))
    {
        return;
    }
    System.out.println(data.intValue());
}
```

## Applying switch statements

### The switch statement

Since Java 14 case values can now be combined:

```java
switch (animal)
{
    case 1,2: System.out.println("lion");
    case 3: System.out.println("dog");
}
```

### Selecting switch data types

boolean, long, float and double are not allowed as the switch statement target variable type.

### Determining acceptable case values

Only literals, constants and expressions that can be evaluated at compile time can be used as values for case statements.

```java
final int bananas = 1;
int apples = 0;
final int cookies = getCookies();

int animals = 1;
switch (animals)
{
    case bananas:
    case apples:        // does not compile
    case getCookies():  // does not compile
    case cookies:       // does not compile
    case 3 * 5:
}
```

### The switch expression

As of Java 14 switch expressions can be used to return a value, giving that every case and default options return a value with the same type as the target variable.

Switch expressions can have blocks or just expressions.

```java
int result = switch(variableToTest)
{
    case constantExpression -> 5;
    case constantExpression -> {
        yield 10;
    }
    default -> 20;
};
```

yield is used as a "return" clause inside a case block.

### Adding optional labels

Optional labels can be added to any control flow statement as an identifier to that statement. Can be useful when dealing with nested loops.

They are declared by an identifier followed by a colon (:) in uppercase snake case.

```java
OUTER_LOOP: 
for (int[] mySimpleArray : myComplexArray)
{
    INNER LOOP:
    for (int i : mySimpleArray)
    {
        // ...
    }
}
```

### The break statement

When using optional labels the break statement can break a specific label.

When not using optional labels the break statement will interrupt the nearest loop.

### The continue statement

The continue statement also supports optional labels.
