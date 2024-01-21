# Operators

## Applying unary operators

### Increment and decrement operators

| Operator | Example | Description |
| - | - | - |
| Pre-increment | ++w | Increases the value and returns the new value |
| Pre-decrement | --w | Decreases the value and returns the new value |
| Post-increment | w++ | Increases the value and returns the original value |
| Post-decrement | w-- | Decreases the value and returns the old value |

```java
int a = 0;
System.out.println(a); // 0
System.out.println(++a); // 1
System.out.println(a); // 1
System.out.println(a--); // 1
System.out.println(a); // 0
```

## Working with binary arithmetic operators

### Numeric promotion

- If two values have different data types, Java will automatically promote one of the values to the larger of the two data types.
- If one of the values is integral and the other is a floating-point, Java will automatically promote the integral value to the floating-point value's data type.
- Smaller data types, namely, byte, short and char, are first promoted to int any time they're used with a Java binary operator with a variable (as opposed to a value), even if neither of the operators are int.
- After all promotion has occurred and the operators have the same data type, the resulting value will have the same data type as its promoted operands.

```java
int x = 1;
long y = 33;
var z = x + y; // long
```

```java
double x = 39.21;
float y = 2.1f;
var z = x + y; // double
```

```java
short x = 10;
short y = 3;
var z = x + y; // int
```

## Assigning values

### Return value of assignment operators

The result of an assignment is an expression in and of itself equal to the value of the assignment.

```java
int a = 10;
int b = (a = 3);

System.out.println(a); // 3
```

## Comparing values

### Logical operators

| & (and) | \| (or) | ^ (xor) |
| - | - | - |
| true if both values are true | true if either value is true | true if only one value is true |

### Conditional operators

Conditional operators are considered short-circuit operators, since the right side of the expression might never be evaluated if the final result can be determined by the left side of the expression.

```java
Duck duck = null;

if (duck != null & duck.getAge() < 5) // NullPointerException
{
    // do something
}

if (duck != null && duck.getAge() < 5)
{
    // do something
}
```

### Checking for unperformed side effects

The short-circuit behaviour can prevent side effects based on the position of state-altering code inside the expression.

```java
int rabbit = 6;
boolean bunny = (rabbit >= 6) || (++rabbit <= 7);
System.out.println(rabbit); // 6
```
