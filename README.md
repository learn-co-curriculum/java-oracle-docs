# Oracle Java Documentation

## Learning Goals

- Introduce the Oracle Java Documentation.
- Explain how to read the Java docs.

## Oracle Java Documentation

Previously, we have mentioned Java having documentation. So let's talk about
this documentation finally!

The official documentation for Java can be found at
[docs.oracle.com](https://docs.oracle.com/en/java/javase/17/docs/api/). Make
sure you are looking at the right version of Java when you look up the
documentation. In these lessons, we have been using Java 17, which is one of
Java's long-term support (LTS) versions. But if ever using a different version,
make sure you specify the version to ensure you are looking at the right
documentation.

A quick way to look up different classes is to type the java version into
the search engine along with the class. For example, if we were looking for
the java documentation on `ArrayList`, we could type this into our search
engine of choice:

```text
Java 17 ArrayList
```

The official Oracle Java Documentation is likely to be one of the first search
results. Double-check the URL for "https://docs.oracle.com" and the version to
be sure.

## Reading the Java Docs

Now that we know what generics and generic boundaries are, we can properly
understand and read the official java documentation! If we were to look at the
documentation, let's choose the `ArrayList` class as an example, we can see
what package the class is in, what parameterized types it takes in, a summary
of the class, and a detailed list and summary of all the constructors and
methods.

![ArrayList Add Methods](https://curriculum-content.s3.amazonaws.com/java-mod-3/java-docs/ararylist-java-docs.PNG)

[ArrayList Java Doc](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html)

Above is a screenshot that shows some methods in the `ArrayList` Java Docs. We
can see that these documentations heavily use generics, especially when
referring to various data structures.

Let's break down a few of these methods, just so we are aware of how to read
them:

- The first method is `add(int index, E element)` and in the description it
  says this method will insert the specified element at the specified position
  in this list. This method will also not return anything, as we can see by the
  `void` return type.
  - It should be noted that these method definitions can use just `E` since `E`
    is part of the generic class definition.
  - Depending on how we instantiated our `ArrayList`, we can add any element of
    the appropriate type into the list at a specified location. The specified
    location is at a certain index within the `ArrayList`. Let's look at an
    example:

```java
import java.util.ArrayList;

public class ArrayListExample {

    public static void main(String[] args) {
        ArrayList<String> myList = new ArrayList<String>();
        myList.add(0, "Hello World!");    // Will add the String at index 0
        myList.add(1, "It's a beautiful day!");    // Will add the String at index 1
    }
}
```

- The second method is the `add(E e)` method that we have used before! We will
  skip over this method since we have already seen it.
- The third method is one that we haven't quite seen yet before:
  `addAll(int index, Collection<? extends E> c)`. This method will add all the
  elements in the specified `Collection` into the list starting at the specified
  position. This method will also return a `boolean` if the `Collection` was
  successfully inserted.
  - The collection we are adding to the `ArrayList` must be of the same type
    or a subclass of the `ArrayList`. In the example below, let's add the
    collection to the front of the list by specifying an index position of 0:

```java
import java.util.Arrays;
import java.util.ArrayList;

public class Example {

    public static void main(String[] args) {
        ArrayList<Double> myList = new ArrayList<Double>(Arrays.asList(
            11.25,
            9.0,
            7.2
        ));

        ArrayList<Double> anotherList = new ArrayList<Double>();
        anotherList.add(0.0);
        anotherList.addAll(0, myList);
    }
}
```

- The last method, `addAll(Collection<? extends E> c)`, will append a
  `Collection` of elements to the list and return a `boolean` if the
  `Collection` was successfully added to the `ArrayList`.
  - This is similar to the last method we looked at, except it will not specify
    where at in the `ArrayList` we want to insert the `Collection`. It will
    simply just add the `Collection` to the end of the list.
  - Let's play around with the generics a little in the next example and see if
    we can add a `List` of `Integer` values to an `ArrayList` of `Number`
    values:

```java
import java.util.Arrays;
import java.util.ArrayList;

public class Example {

    public static void main(String[] args) {
        ArrayList<Integer> myList = new ArrayList<Integer>(Arrays.asList(
            11,
            18,
            34
        ));

        ArrayList<Number> anotherList = new ArrayList<Number>();
        anotherList.add(0);
        anotherList.addAll(myList);

        for (Number num : anotherList) {
            System.out.println(num);
        }
    }
}
```

Sure enough, the code above will compile and execute to the following output:

```text
0
11
18
34
```

## Conclusion

Looking at the Java docs is especially helpful for when you can't remember a
certain method in a class, how to construct a certain object, or you need to
read up on a class and its purpose! Take some time to explore some more of the
java documentation of classes and interfaces we may have already covered.

## Resources

- [Oracle Java 17 Docs Overview](https://docs.oracle.com/en/java/javase/17/docs/api/)
- [ArrayList Java Doc](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/ArrayList.html)
