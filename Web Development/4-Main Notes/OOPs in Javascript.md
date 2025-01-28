
**Status:**  #Complete 
**Tags:**  [[Backend]] [[frontend]] [[OOPs]]
# JavaScript OOP (Object-Oriented Programming)

## Summary Sheet

### Q1: What is Object-Oriented Programming (OOP)?
**A:** Object-Oriented Programming (OOP) is a programming paradigm in computer science that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects.

### Q2: What are some benefits of using OOP in JavaScript?
**A:** Some benefits of using OOP in JavaScript include:
- Improved code organization (structure of code)
- Reusability of code
- Better maintainability of code
- Closeness to real-world objects

### Q3: What is the difference between an object and a class in JavaScript?
**A:** 
- **Object:** A standalone entity with properties, methods, and a type. It can be created directly from functions or through constructor functions.
- **Class:** Acts as a blueprint for creating objects.

### Q4: What is a constructor function in JavaScript?
**A:** A constructor function is a special function that is used to create and initialize objects in JavaScript. When a new object is created using a constructor function, it is automatically assigned a set of properties and methods defined within the function.

### Q5: What is a prototype chain in JavaScript?
**A:** Every object in JavaScript has a built-in property called its prototype. The prototype is itself an object, so it has its own prototype, creating a **prototype chain**. This chain ends when a prototype has `null` as its own prototype.

### Q6: What is the difference between a constructor and a class in JavaScript?
**A:** 
- **Constructor:** A function that creates an object. 
- **Class:** A blueprint for creating objects. Classes define the framework, whereas the constructor creates and initializes the objects.  
  *(Note: In JavaScript, classes are syntactic sugar over constructor functions.)*

### Q7: Why is the `new` keyword used in JavaScript?
**A:** The `new` keyword is used to create an instance of an object. When used with a constructor function, it:
1. Creates a new object.
2. Sets the constructor function's `this` keyword to point to the new object.

### Q8: What is Inheritance in OOP?
**A:** Inheritance in OOP is the ability of a class to derive properties and characteristics from another class while having its own properties as well.

### Q9: What is the `super` keyword in JavaScript?
**A:** The `super` keyword in JavaScript acts as a reference variable to the parent class. It is mainly used to access a variable, method, or constructor in the base class from the derived class.

### Q10: Example Code
**Q:** What will be the output for the following code?  
```javascript
class Box {
  area() {
    return "Box area";
  }
}

class Square extends Box {
  area() {
    return "Square area is 16";
  }
}

const obj = new Square();
console.log(obj.area());
