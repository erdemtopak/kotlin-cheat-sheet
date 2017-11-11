Kotlin Cheat Sheet
==================

# 1. Constructor

### Extend a class which has multiple constructors.

```Kotlin
open class Parent {

    constructor(name: String) {
        //...
    }

    constructor(name: String, surname: String) {
        //...
    }
}

class Child : Parent {

    constructor(name: String) : this(name, "") { //Calls the constructor below
        //...
    }

    constructor(name: String, surname: String) : super(name, surname) { //Calls Parent's constructor
        //...
    }
}
``` 

### Chain constructor code can be generated by Kotlin with **@JvmOverloads** annotation

Assume that we have a class Person written in Java.
```Java
class Person {

	Person(String name) {
		this(name, "")
	}

	Person(String name, String surname) {
		this(name, "", 0)
	}

	Person(String name, String surname, int age) {
		//implementation
	}
}
```

Kotlin version will be
```Kotlin
class Person @JvmOverloads constructor(
	var name: String,
	var surname: String = "",
	var age: Int = 0 
)
```