---
layout: post
title: Functional Java Features
date: 2023-03-23 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: java.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [jva]
---

Java Streams are a powerful feature introduced in Java 8 that allows you to perform complex operations on collections of objects. Streams provide a way to manipulate and process data in a functional style, using a fluent and concise syntax. In this post, we'll explore what Java Streams are, how they work, and some code examples to help you get started.

What are Java Streams?
Java Streams are a sequence of elements that can be processed in a functional style. Streams provide a way to express complex operations on collections of objects without the need for explicit iteration. Instead, Streams allow you to define a pipeline of operations that are applied to each element of the Stream in a lazy and efficient manner.

There are two types of operations in a Stream pipeline: intermediate and terminal operations. Intermediate operations transform the elements of a Stream into another Stream, while terminal operations produce a result or a side-effect, such as printing output to the console.

### How do Java Streams work?

Java Streams are created from a source, such as a collection, an array, or an I/O channel. Once a Stream is created, a sequence of intermediate operations can be applied to transform the elements of the Stream into another Stream. These intermediate operations are evaluated lazily, meaning they are only executed when a terminal operation is invoked.

Once the Stream pipeline is defined, a terminal operation is used to produce a result. Terminal operations are eager, meaning they are executed immediately and produce a result or a side-effect.

Here's an example that shows how to create a Stream from a collection of integers, filter out even numbers, and print the result to the console:

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
numbers.stream()
.filter(n -> n % 2 == 0)
.forEach(System.out::println);
```

In this example, the numbers collection is converted to a Stream using the stream() method. The filter() method is used to create a new Stream that contains only even numbers, and the forEach() method is used to print each element to the console.

### Code Examples

Here are some code examples that demonstrate some of the most common operations you can perform on a Stream.

### Creating a Stream

You can create a Stream from a collection, an array, or a range of values.

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
Stream<String> stream = names.stream();

int[] numbers = {1, 2, 3, 4, 5};
IntStream intStream = Arrays.stream(numbers);

Stream<Integer> range = Stream.range(1, 10);
```

### Filtering elements

You can use the filter() method to create a new Stream that contains only elements that satisfy a given predicate.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
Stream<Integer> evenNumbers = numbers.stream().filter(n -> n % 2 == 0);
```

### Mapping elements

You can use the map() method to transform each element of a Stream into another element.

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
Stream<Integer> nameLengths = names.stream().map(String::length);
```

### Reducing elements

You can use the reduce() method to combine all elements of a Stream into a single result.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
int sum = numbers.stream().reduce(0, Integer::sum);
```

In this example, the reduce() method takes two arguments: an initial value and a binary operator. The initial value is 0, and the binary operator is Integer::sum, which is a method reference to the static method sum() of the Integer class. The reduce() method applies the binary operator to each element of the Stream and the result of the previous operation, starting with the initial value.

### Collecting elements

You can use the collect() method to convert a Stream into a collection, such as a List or a Set.

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> filteredNames = names.stream().filter(s -> s.startsWith("A")).collect(Collectors.toList());
```

In this example, the collect() method takes a Collector object that defines how to accumulate elements into a collection. The Collectors.toList() method returns a Collector that accumulates elements into a List.

### Sorting elements

You can use the sorted() method to sort the elements of a Stream.

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
List<String> sortedNames = names.stream().sorted().collect(Collectors.toList());
```

In this example, the sorted() method returns a new Stream that contains the elements of the original Stream in sorted order. The Collectors.toList() method is used to collect the elements into a List.

### Parallel processing

You can use the parallel() method to create a parallel Stream that allows processing elements in parallel.

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);
int sum = numbers.parallelStream().reduce(0, Integer::sum);
```

In this example, the parallelStream() method is used to create a parallel Stream. The reduce() method is used to find the sum of all elements in the Stream, and the binary operator Integer::sum is used to combine the elements.

#### Conclusion

Java Streams provide a powerful and flexible way to process collections of objects in a functional style. Streams allow you to express complex operations using a fluent and concise syntax, and provide lazy evaluation and parallel processing for improved performance. With the examples provided in this post, you should now have a good understanding of what Java Streams are and how to use them in your code.
