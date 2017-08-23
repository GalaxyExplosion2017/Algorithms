## [496 Toy Factory](http://www.lintcode.com/en/problem/toy-factory/)

##### Description

Factory is a design pattern in common usage. Please implement a `ToyFactory` which can generate proper toy based on the given type.

##### Example

```
ToyFactory tf = ToyFactory();
Toy toy = tf.getToy('Dog');
toy.talk(); 
>> Wow

toy = tf.getToy('Cat');
toy.talk();
>> Meow
```

##### Solution

```java
/**
 * Your object will be instantiated and called as such:
 * ToyFactory tf = new ToyFactory();
 * Toy toy = tf.getToy(type);
 * toy.talk();
 */
interface Toy {
    void talk();
}

class Dog implements Toy {
    // Write your code here
    public void talk(){
       System.out.println("Wow");
    }
}

class Cat implements Toy {
    // Write your code here
    public void talk(){
        System.out.println("Meow");
    }
}

public class ToyFactory {
    /**
     * @param type a string
     * @return Get object of the type
     */
    public Toy getToy(String type) {
        // Write your code here
        Toy T = null;
        if(type.equals("Dog"))
            T = new Dog();
        else if(type.equals("Cat"))
            T = new Cat();
        return T;
    }
}
```

