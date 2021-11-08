# java_concept
Java Concept Repo (no coding)

## reference type

a memory address where a given object is stored.

## object assignment

```
Object o = new Object(); // this assign a new object to variable o and generate a new memory address.
```

if you assign a new object to an existing reference variable, the variable hold a new memory address

```
Object o = new Object(); // memory address: 27082746
o = new Object(); // new memory address: XXXXXX
```

## pass by value

java always use 'pass-by-value' even if you pass a reference. it pass a copy of the reference (e.g., a copy of memory address).

this means that you can modify the object (e.g., its fields) in called functions.

```
public class MyClass {
    public static void main(String args[]) {
        Object o = new Object();
        Object h = o;
        
        o.someField = "initial";

        foo(o);
        
        o.someField // "change" since it passes a copy of memory address whicih points to the object.
        
    }
    
    public static void foo(Object o) { 
        // a copy of the memory address so it can access to the object using it and can modify the object.
        o.someField = "change";
    }
    
}

```

but if you assign a new object to an existing reference object in the called function, Java assign a new memory address to the variable so the variable in the called function does not affect the change.

```
public class MyClass {
    public static void main(String args[]) {
        Object o = new Object(); // memory address: X
        Object h = o;
       
        foo(o);
   
        // since a copy of memory address is passed, it does not affect the original variable (e.g., o)
        System.out.println(o == h); // both memory addresses: X
    }
    
    public static void foo(Object o) {
        System.out.println("in method 1st, o: " + o); // memory address: X but this is a copy 
        
        // assign a new memory address to the copy of memory address (e.g., o) when instantiate a new object such as 'new Object()'
        o = new Object(); 
        
        System.out.println("in method 2nd, o: " + o); // memory address: Y 
    }
    
}
```
