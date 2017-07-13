akshaya P R

# Java 8 features
This is classic OOP style of hiding method implementations from the caller. The caller simply passes a variable to the method which then does something with the value of the variable and returns another value or produces a side effect as it is in our case.
```
class LambdaDemo {
    public void printSomething(String something) {
        System.out.println(something);
    }


    public static void main(String[] args) {
        LambdaDemo lambdaDemo = new LambdaDemo();
        String something = "Learning Lambda";
        lambdaDemo.printSomething(something);
    }
}
```
see an equivalent implementation that uses behavior passing other than variable passing. To achieve this, we have to create a functional interface that defines that abstracts the behavior instead of a method. A functional interface is an interface that has only one method:

```package com.kg.lambdaapp;
interface Printer {
    void print(String val);
}

class LambdaDemo {
    public void printSomething(String something, Printer printer) {
        //System.out.println(something);
        printer.print(something);
    }


    public static void main(String[] args) {
        LambdaDemo lambdaDemo = new LambdaDemo();
        Printer printer = new Printer() {
            @Override
            public void print(String val) {
                System.out.println(val);
            }
        };
        String something = "Learning Lambda";
        lambdaDemo.printSomething(something, printer);
    }
}

```

```
public void print(String toPrint) {
                System.out.println(toPrint);
            }
```

lambda expressions

```package com.kg.lambdaapp;
interface Printer {
    void print(String val);
}

class LambdaDemo {
    public void printSomething(String something, Printer printer) {
        //System.out.println(something);
        printer.print(something);
    }


    public static void main(String[] args) {
        LambdaDemo lambdaDemo = new LambdaDemo();
        Printer printer = (String toPrint) -> {
                System.out.println(toPrint);
        };

        String something = "Learning Lambda";
        lambdaDemo.printSomething(something, printer);
    }
}
```

```
(String toPrint) -> {
                System.out.println(toPrint);
        }
```



```
package com.kg.lambdaapp;
interface Printer {
    void print(String something);
}

public class LambdaDemo {
    public static void printSomething(String something) {
        System.out.println(something);
        //printer.print(something);
    }


    public static void main(String[] args) {
        //LambdaDemo lambdaDemo = new LambdaDemo();
        String something = "Learning Lambda";
        Printer printer = LambdaDemo::printSomething;
        printer.print(something);
    }
}
```
```
package com.kg.lambdaapp;
interface Printer {
    void print();
}

public class LambdaDemo {
    public static void printSomething() {
        System.out.println("something");
        //printer.print(something);
    }

    public static void main(String[] args) {
        //LambdaDemo lambdaDemo = new LambdaDemo();
        String something = "Learning Lambda";
        Printer printer = LambdaDemo::printSomething;
        printer.print();
    }
}
```
end
 Sindhuja.R,Saritha.R
 
Stream Min()

Description

Returns the minimum element of this stream according to the provided Comparator. This is a special case of a reduction.

This is a terminal operation.

Syntax

Optional<T> min(Comparator<? super T> comparator)
Parameters:

comparator - a non-interfering, stateless Comparator to compare elements of this stream
Returns:

An Optional describing the minimum element of this stream,or an empty Optional if the stream is empty
Throws:

NullPointerException - if the minimum element is null 
Code

  List<String> list = Arrays.asList("Gza","Gzb","Gox","Elephant");
	String min = list.stream().min(Comparator.comparing(String::valueOf)).get();
	System.out.println("Min:"+ min);
Stream Max()

Description

Returns the maximum element of this stream according to the provided Comparator.This is a special case of a reduction.
This is a terminal operation.
Syntax

Optional max(Comparator<? super T> comparator) Parameters

comparator - a non-interfering, stateless Comparator to compare elements of this stream
Returns:

An Optional describing the maximum element of this stream, or an empty Optional if the stream is empty
Throws:

NullPointerException - if the maximum element is null 

Code

  List<String> list = Arrays.asList("Gza","Gzb","Gox","Elephant");
   String max = list.stream().max(Comparator.comparing(String::valueOf)).get();
   System.out.println("Max:"+ max);
  
Stream distinct()

Description

It removes the duplicate elements in the list
Syntax

Stream<T> distinct()
Code

Collection<String> list = Arrays.asList("A", "B", "C", "D", "A", "B", "C");
List<String> distinctElements = list.stream().distinct().collect(Collectors.toList());
System.out.println(distinctElements);
