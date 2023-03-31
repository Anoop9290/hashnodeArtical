---
title: "All About Equals method in Java"
datePublished: Fri Feb 03 2023 19:55:09 GMT+0000 (Coordinated Universal Time)
cuid: cldoy48pr00000albdbfdax29
slug: what-is-equals-method-in-java
tags: equals

---

Hi Guys this is Anoop, I am starting my blogging journey with basic topics of Java.  
Please feel free to write your reviews.

### **Introduction**

As we all know there is an Object class in Java. who is the parent of each class by default? This Object class comes with some methods, the public boolean equals(Object) method is one of them. The equals method is used when we compare the equality of two objects. The default implementation of the equals method is that it compares object the same as the '==' operator does.

We need to override the equals method if we want to change this behaviour.

### Implementation

Please see the below example.

```java
public class Circle {

    int radius;
    public Circle(int radius) {
        this.radius = radius;
    }


    public static void main(String[] args) {

        Circle c1 = new Circle(12);

        Circle c2 = new Circle(12);

        Circle c3 = c2;

        System.out.println(c1.equals(c2));//false
        System.out.println(c1 == c2);//false

        System.out.println(c2 == c3);//true
        System.out.println(c3.equals(c2));//true

    }
}
```

We can override the equals method in the Circle class and change the behaviour of the above implementation.

Please see the below example.

```java
public class Circle {

    int radius;

    public Circle(int radius) {
        this.radius = radius;
    }

    @Override
    public boolean equals(Object object) {
        Circle other = (Circle) object;
        if (this.radius != other.radius)
            return false;
        return true;
    }

    public static void main(String[] args) {

        Circle c1 = new Circle(12);

        Circle c2 = new Circle(12);

        Circle c3 = c2;

        System.out.println(c1.equals(c2));//true
        System.out.println(c1 == c2);//false

        System.out.println(c2 == c3);//true
        System.out.println(c3.equals(c2));//true

    }
}
```

**Note** *that this is a basic implementation of equals, there more things are left to do in the above implementation to make it the foolproof*

**Any equals implementation should satisfy these properties:**

1. Reflexive. For any reference value x, x.equals(x) returns true
    
2. Symmetric. For any reference values x and y, x.equals(y) should return true if and only if y.equals(x) returns true.
    
3. Transitive. For any reference values x, y, and z, if x.equals(y) returns true and y.equals(z) returns true, then x.equals(z) must return true.
    
4. Consistent. For any reference values x and y, multiple invocations of x.equals(y) consistently return true or consistently return false, if no information used in equals is modified.
    
5. For any non-null reference value x, x.equals(null) should return false.
    

I hope now it is clear about equals method. If you still have any doubts let me know in comments. or by dropping mail tiwari.anoop@outlook.com.