# SOLID

The SOLID principles are a set of design principles for object-oriented programming intended to make software designs more understandable, flexible, and maintainable. The principles are intended to help developers create code that is easier to maintain and less prone to bugs.

## SRP: Single Responsibility Principle
– Each part of the system must have only one reason to change.

In other words, a class should have only one responsibility. For example, let's say we have a class called Employee that is responsible for managing employee data, printing reports, and managing employee payroll. In this case, we should consider splitting the Employee class into three separate classes for each responsibility.

Example code that demostrates how to apply the SRP:

```java
public class Product {
    private String name;
    private double price;
    private double weight;

    // Constructor, getters, and setters

    public double calculatePrice() {
        // Calculation logic
        return price;
    }

    public double getShippingCost() {
        // Shipping logic
        return shippingCost;
    }

    public void addToCart(ShoppingCart cart) {
        // Add to cart logic
    }
}

public class Pricing {
    public double calculatePrice(Product product) {
        // Calculation logic
        return price;
    }
}

public class Shipping {
    public double getShippingCost(Product product) {
        // Shipping logic
        return shippingCost;
    }
}

public class ShoppingCart {
    private List<Product> items;

    // Constructor, getters, and setters

    public void addItem(Product product) {
        // Add item logic
    }

    public void removeItem(Product product) {
        // Remove item logic
    }

    public double calculateTotalPrice() {
        // Calculation logic
        return totalPrice;
    }
}

```

In this example , we've separated the responsibilities for pricing and shipping into separate classes, as well as cart functionality into a separate class. The Product class is now only responsible for representing a product and is no longer responsible for pricing, shipping, or cart functionality. By doing so, we adhere to the SRP principle by ensuring that each class has only one responsibility or reason to change.

## OCP: Open-Closed Principle

This principle states that for a software system to be easy to change, those changes must be done through adding new code, not changing existing code.

In other words, we should be able to add new functionality to a system by creating new code, rather than changing existing code. For example, suppose we have a class named Vehicle that has a method named calculateSpeed(). If we want to add a new type of vehicle, such as a skateboard, we can extend the Vehicle class and implement the calculateSpeed() method for the skateboard without modifying the existing code.

Here is an example in Java that demonstrates the Open-Closed Principle (OCP):

```java
public abstract class PaymentMethod {
    public abstract void pay(double amount);
}

public class CreditCardPayment extends PaymentMethod {
    public void pay(double amount) {
        // Credit card payment logic
    }
}

public class PaypalPayment extends PaymentMethod {
    public void pay(double amount) {
        // Paypal payment logic
    }
}

public class PaymentProcessor {
    private PaymentMethod paymentMethod;

    public void processPayment(double amount) {
        paymentMethod.pay(amount);
    }

    public void setPaymentMethod(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod;
    }
}

```

In this example, we have an abstract class called PaymentMethod that represents a payment method. This class has an abstract method called pay() that represents the payment logic, which is implemented in the concrete classes CreditCardPayment and PaypalPayment.

The PaymentProcessor class follows the Open-Closed Principle by being closed for modification but open for extension. This means that we can add new payment methods by creating new classes that extend PaymentMethod and implement the pay() method. The PaymentProcessor class can work with any payment method as long as it extends PaymentMethod and implements the pay() method.

By following the OCP, we can easily add new payment methods without modifying the existing code. This helps to keep the code clean, maintainable, and flexible.

## LSP: Liskov Substitution Principle

To build a software system from interchangeable parts, the parts must adhere to a contract which allows the parts to be interchangeable.

This principle states that derived classes should be substitutable for their base classes, meaning they should behave in the same way as the base class without any surprises. 

For example, let's say we have a class named Animal with a method called makeSound(). We can extend the Animal class to create a Dog subclass that also has a makeSound() method. However, if the Dog subclass throws an error when makeSound() is called, it violates the LSP.

Here is an example in Java that demonstrates the Liskov Substitution Principle (LSP):

```java
public class Shape {
    protected int width;
    protected int height;

    public Shape(int width, int height) {
        this.width = width;
        this.height = height;
    }

    public int getArea() {
        return width * height;
    }
}

public class Rectangle extends Shape {
    public Rectangle(int width, int height) {
        super(width, height);
    }
}

public class Square extends Shape {
    public Square(int sideLength) {
        super(sideLength, sideLength);
    }
}

public class AreaCalculator {
    public static int calculateArea(Shape shape) {
        return shape.getArea();
    }
}


```

In this example , we have a class called Shape that represents a two-dimensional shape. It has width and height fields as well as a getArea() method that calculates its area. We have two subclasses that inherit from Shape: Rectangle and Square.

Even though a square "is-a" rectangle in natural language, it violates the Liskov Substitution Principle because a square cannot replace a rectangle in all situations. For example, if we have a method that expects a rectangle and sets its width to 5 and height to 4, a square cannot be substituted because its width and height must be the same.

By designing our classes in this way, we adhere to the Liskov Substitution Principle, ensuring that a subclass can always be used in place of its superclass without introducing unexpected behavior.

## ISP: Interface Segregation Principle

Don't depend on things you don't use. 

This principle states that classes should not be forced to depend on interfaces they do not use. Instead, classes should only have to depend on the interfaces they actually use. 

For example, consider a class named Car that implements the interface Vehicle. However, the Car class does not need all the methods in the Vehicle interface, such as fly() or sail(). In such a case, we should create a separate interface that only includes the methods that are needed by the Car class.

Here is an example in Java that demonstrates the Interface Segregation Principle (ISP):

```java
interface Human {
    void eat();
    void sleep();
    void work();
}

// Violating the ISP
class Manager implements Human {
    public void eat() {
        System.out.println("Manager eats");
    }
    public void sleep() {
        System.out.println("Manager sleeps");
    }
    public void work() {
        System.out.println("Manager manages employees");
    }
}

// Adhering to the ISP
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

interface Sleepable {
    void sleep();
}

class Employee implements Workable, Eatable, Sleepable {
    public void work() {
        System.out.println("Employee works");
    }
    public void eat() {
        System.out.println("Employee eats");
    }
    public void sleep() {
        System.out.println("Employee sleeps");
    }
}

```

In this example , we have an interface called Human that has three methods: eat(), sleep(), and work(). We then create a class called Manager that implements the Human interface.

However, the Manager class violates the Interface Segregation Principle because not all humans are managers and not all humans manage employees. This means that the Manager class is forced to implement methods that it may not need, which violates the principle.

To adhere to the ISP, we can break the Human interface into three individual interfaces that define the specific behaviors that we need: Workable, Eatable, and Sleepable. We can then create a class called Employee that implements all three of these interfaces.

By adhering to the ISP, we ensure that our classes are more focused and not bloated with unnecessary methods. This makes our code more modular and easier to maintain over time.


## DIP: Dependency Inversion Principle

Code that implements high-level policy should not depend on code that implements low-level details.

This principle states that high-level modules should not depend on low-level modules. Instead, both should depend on abstractions. Additionally, abstractions should not depend on details. Instead, details should depend on abstractions. 

For example, suppose we have an application that depends on a database. Instead of directly using a specific database implementation, we can create an interface that abstracts the implementation details of the database. This way, the high-level modules in our application can depend on the abstraction (the interface), and the low-level module (the database implementation) can depend on the abstraction as well. 

Here is an example in Java that demonstrates the Dependency Inversion Principle (DIP):

```java
interface Database {
    void saveData(String data);
}

class MySQLDatabase implements Database {
    public void saveData(String data) {
        System.out.println("Data saved to MySQL database: " + data);
    }
}

class OracleDatabase implements Database {
    public void saveData(String data) {
        System.out.println("Data saved to Oracle database: " + data);
    }
}

class Application {
    private Database database;
    
    public Application(Database database) {
        this.database = database;
    }
    
    public void doSomething() {
        database.saveData("Some data to be saved");
    }
}


```

In this example , we have an interface called Database that defines a saveData() method. We then have two classes, MySQLDatabase and OracleDatabase, that implement the Database interface.

We then have a class called Application that depends on the Database interface rather than any specific implementation of the database. This way, the high-level Application class is not coupled to the low-level details of any specific database implementation.

By adhering to the DIP, we ensure that our code is more flexible and easier to maintain over time. If we decide to switch from using MySQL to Oracle (or any other database), we can simply pass in the appropriate implementation of the Database interface to the Application class without having to make changes to the Application class itself.

# Other software design FAQ

## SOLID design principles vs software design patterns
The SOLID principles are guidelines for developing software that are intended to make your code more maintainable, flexible, and scalable. They are not specific to any particular language or framework, and can be applied to software development in general.

On the other hand, design patterns are specific solutions to common problems that developers face while building software. They are based on common scenarios and have been tried and tested in various projects over time.


## Why favor composition over inheritance
Here are some reasons why this principle is beneficial:

* Encapsulation: Inheritance can expose a subclass to implementation details of its parent class. This can lead to tight coupling and can make it harder to modify and extend the code. Composition, on the other hand, allows for better encapsulation, as objects can interact through well-defined interfaces instead of directly accessing each other's methods and properties.

* Flexibility: Inheritance creates a rigid hierarchy that can be difficult to modify once established. In contrast, composition allows for greater flexibility in building objects, as it is easier to add or remove components as needed.

* Reusability: Inheritance can result in a lot of redundant code, as subclasses inherit methods and properties from their parent classes that may not be relevant to their specific use case. Composition allows for greater reusability of code, as objects can be constructed from smaller, more modular components that can be used across different objects and contexts.

* Testing: Inheritance can make it harder to test individual components in isolation, as the behavior of a subclass can be influenced by the implementation details of its parent class. Composition, on the other hand, allows for easier testing of individual components, as objects can be mocked or substituted as needed.