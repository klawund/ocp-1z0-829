# Core APIs

## Understanding equality

### String pool

Only string literals and compile-time constants are stored in the string pool. Anything that depends on runtime to be calculated creates a new instance.

```java
var a = "hello world";
var b = "hello" + " world";

System.out.println(a == b); // true;

var c = new StringBuilder("hello world");

System.out.println(a == c.toString()); // false
```

## Understanding arrays

### Creating an array of primitives

The placement of the bracet in the array declaration is arbitrary, allowing for it to be placed before or after the reference name. All of these are valid declarations:

```java
int[] a;
int [] b;
int []c;
int d[];
int e [];
```

When declaring more than one reference in the same declaration, placement matters.

```java
int[] a, b; // a = int[] b = int[]
int a[], b; // a = int[] b = int
```

### Searching

Binary search is implemented in the Arrays' API class. The outcome of a binary search can only be interpreted assertively if the array is sorted.

| Scenario | Result |
|-|-|
|Target element found in sorted array|Index of match|
|Target element not found in sorted array|Negative value showing one smaller than the negative of the index, where a match needs to be inserted to preserve sorted order|

### Comparing

#### Using compare()

The result of compare is interpreted the same as the result of a Comparator implementation.

- A negative number means the first array is smaller than the second.
- Zero means both are equal.
- A positive number means the first array is larger than the second.

#### Using mismatch()

If the arrays are equal -1 is returned. If the arrays differ the index of the first mismatch is returned.

## Working with dates and times

Important to note that all new classes of the Java 8 Date Time API are thread safe and therefore immutable.

### Creating dates and times

|Class|Meaning|
|-|-|
|LocalDate|Contains just a date - no time and no time zone|
|LocalTime|Contains just a time - no date and no time zone|
|LocalDateTime|Contains both a date and a time but no time zone|
|ZonedDateTime|Contains a date, a time and a time zone|

All have factory methods:

```java
// LocalDate.of(year, month, day)
var a = LocalDate.of(2022, Month.JANUARY, 20);
var b = LocalDate.of(2022, 1, 20);

// LocalTime.of(hours, minutes, seconds, nano)
var c = LocalTime.of(6, 15);
var d = LocalTime.of(6, 15, 30, 750);

// LocalDateTime.of(year, month, day, hours, minutes, seconds, nano)
var e = LocalDateTime.of(2022, Month.JANUARY, 20, 6, 15, 30);

// LocalDateTime.of(LocalDate, LocalTime)
var d = LocalDateTime.of(a, c);
```

ZonedDateTime takes a ZoneId instance as parameter. ZoneId's have identifiers and are retrieved by their identifiers through factory methods.

```java
var zone = ZoneId.of("US/Eastern");

// ZonedDateTime.of(year, month, day, hours, minutes, seconds, nano, zone)
var zoned1 = ZonedDateTime.of(2022, 1, 6, 15, 30, 750, zone);

// ZonedDateTime.of(LocalDate, LocalTime, ZoneId)
var zoned2 = ZonedDateTime.of(date1, time1, zone);

// ZonedDateTime.of(LocalDateTime, ZoneId)
var zoned3 = ZonedDateTime.of(dateTime1, zone);
```

There are no overloads for ZonedDateTime.of() that takes Month as parameter.
