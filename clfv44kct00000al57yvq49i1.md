---
title: "Difference between Comparable and Comparator"
datePublished: Thu Mar 30 2023 12:49:23 GMT+0000 (Coordinated Universal Time)
cuid: clfv44kct00000al57yvq49i1
slug: difference-between-comparable-and-comparator
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/aOC7TSLb1o8/upload/c464f016a99e0e74e8162c431c773d93.jpeg
tags: java-comparable

---

### Introduction:

In Java, the `Comparator` and `Comparable` interfaces are widely used for sorting and ordering objects. Both interfaces provide a mechanism to define the comparison behavior of objects, but they differ in the way they are used and implemented.

In this blog, we will explore the differences between `Comparator` and `Comparable` interfaces, how they are used, and when to use them.

### Comparable Interface:

The `Comparable` interface is a built-in interface in the Java programming language that defines a single method called `compareTo()`. This method is used to compare two objects of the same class and return an integer value indicating their relative ordering.

To use the `Comparable` interface, a class must implement the interface and override the `compareTo()` method. The method should return a negative integer if the object is less than the argument, a positive integer if the object is greater than the argument, and zero if the object is equal to the argument.

For example, suppose we have a class called `Person` with a `name` and `age` field. To implement the `Comparable` interface for the `Person` class, we can define the `compareTo()` method as follows:

```java
arduinoCopy codepublic class Person implements Comparable<Person> {
    private String name;
    private int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    @Override
    public int compareTo(Person other) {
        return this.age - other.age;
    }
}
```

In this example, the `compareTo()` method compares two `Person` objects based on their `age` field. If the `age` of the current object is less than the `age` of the argument object, the method returns a negative integer. If the `age` of the current object is greater than the `age` of the argument object, the method returns a positive integer. If the `age` of the current object is equal to the `age` of the argument object, the method returns zero.

### Comparator Interface:

The `Comparator` interface is also a built-in interface in the Java programming language that defines two methods called `compare()` and `equals()`. Unlike the `Comparable` interface, which is implemented by the class whose objects need to be sorted, the `Comparator` interface is implemented by a separate class that provides a comparison behavior for a particular field or property of an object.

To use the `Comparator` interface, we create a separate class that implements the interface and overrides the `compare()` method. This method takes two arguments, which are the objects to be compared, and returns an integer value indicating their relative ordering.

For example, suppose we have a class called `Person` with a `name` and `age` field. To define a `Comparator` for the `Person` class that compares objects based on their `name` field, we can define a separate class as follows:

```java
javaCopy codepublic class PersonNameComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return p1.getName().compareTo(p2.getName());
    }
}
```

In this example, the `compare()` method compares two `Person` objects based on their `name` field by calling the `compareTo()` method of the `String` class.

When to use Comparable and Comparator?

The `Comparable` interface is typically used when we want to define a natural ordering for a class, such as sorting numbers in ascending order, sorting names alphabetically, or sorting dates chronologically.

The `Comparator` interface is typically used when we want to define a custom ordering for a class, such as sorting `Person` objects based on their `name` field or sorting `Book` objects based on their \`price