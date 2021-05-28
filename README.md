<h1 align="center">Learning Android</h1>
<p align="center">
 
<h2 align="center">onClick</h2>

We made a button in XML and defined it's onClick property which when we go to Java will allows us to make it 

into a function that when the button is clicked the function clickFunction is then called upon.

```
 public void clickFunction(View view){
 
CODE

}

```

We had to import the View.

```
import android.view.View;
```

<h4 align="center">Button</h4>

```
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="clickFunction" // We now defined an onClick function called clickFunction
        android:text="button"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
```

![1](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-07%20at%2012.23.56%20AM.png)

we're putting a line of code into Log, the log tells us what is going on behind the scenes when the app is running.

So we're putting a type of log called "i" for info, which tells you certaion information about your application.

We add a tag that describes the log, and we can display that message in the Logcat.

<h4 align="center">Log</h4>

```
public void clickFunction(View view){
    Log.i("info", "Button is pressed")
}
```

OUTPUT:
![2](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-03-06%20at%2010.44.28%20PM.png)


<h4 align="center">EditText</h4>

```
<EditText
        android:id="@+id/nameEditText" //Edit text ID
        android:layout_width="406dp"
        android:layout_height="67dp"
        android:layout_marginBottom="51dp"
        android:ems="10"
        android:hint="Your Name?"
        android:inputType="textPersonName"
        android:text="Name"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.4"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="1.0" />
```

![3](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-07%20at%2012.24.07%20AM.png)

To see what the user enters in the EditText box the log when the button is pressed we need to include it in the onCLick function we made

We first need to make a EditText variable which has a type of `EditText` we will name it `nameEditText` and we'll set it equal to 

the EditText box view and we'll need to use `findViewById()` to find that view. We need to use `R` to be able to acess resources

and then we specify `id` and then the name of the EditText box id we made which is `nameEditText`.

```
EditText nameEditText = (EditText) findViewById(R.id.nameEditText);//it will return a view so we want to convert the View into an 
                                                                     EditText
```

```
 public void clickFunction(View view){
        EditText nameEditText = (EditText) findViewById(R.id.nameEditText);
        Log.i("info", "Button is pressed");
        Log.i("Values" , nameEditText.getText().toString()); //gets the value of the variable nameEditText, then we convert it to a string!

    }
```
![4](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-07%20at%2012.38.36%20AM.png)
![5](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-07%20at%2012.06.06%20AM.png)

<h2 align="center">Example</h2>

<h4 align="center">XML</h4>


```
<EditText
        android:id="@+id/editTextTextUserName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="10"
        android:inputType="textPersonName"
        android:hint="Enter Username"
        app:layout_constraintBottom_toTopOf="@+id/editTextPassword"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/editTextPassword"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="Enter Password"
        android:inputType="textPassword"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.502"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Button"
        android:onClick="loginButtonOnClick"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextPassword" />
```

<h4 align="center">Java</h4>

```
    public void loginButtonOnClick(View view){
        EditText userNameEditText = (EditText)(findViewById(R.id.editTextTextUserName));
        EditText passwordEditText = (EditText)(findViewById(R.id.editTextPassword));

        Log.i("info", "Button Clicked");

        Log.i("UserName", userNameEditText.getText().toString());
        Log.i("Password", passwordEditText.getText().toString());
    }
```
<h4 align="center">User Interface</h4>

![6](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-07%20at%201.41.29%20PM.png)

<h4 align="center">Log Cat</h4>

![7](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-07%20at%201.41.51%20PM.png)


<h4 align="center">Toast</h4>


To use the Toast features you have to import the Toast class first
```
import android.widget.Toast;
```
You can display a pop up using toast by using the following
```
Toast.makeText(<context>,<display message>, <Toast.LENGTH_SHORT>).show();
```
Displays the text typed in the ```EditText``` box.
```
Toast.makeText(this,"Hello "+userNameEditText.getText().toString(), Toast.LENGTH_SHORT).show();
```

![8](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-14%20at%2012.38.06%20PM.png)

<h4 align="center">ImageView</h4>

```
 <ImageView
        android:id="@+id/imageView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:scaleType="fitCenter"
        android:src="@drawable/aot"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintVertical_bias="0.551" />
```

![9](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/ImageView.png)

We can use the onClick function from the button to change the image of the ImageView.

We use `setImageResource(R.id.<filename>);` to change the image of the `ImageView`
Example
```
public void buttonOnClick(View view){
        ImageView image = (ImageView) (findViewById(R.id.imageView));
        image.setImageResource(R.drawable.eren);
    }
```
<h2 align="center">Example of changing an image onClick</h2>

![10](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/ImageChange.gif)

<h1 align="center">Currency Changing Application</h1>

<h2 align="center">XML</h2>

```
<ImageView
        android:id="@+id/imageViewMoney"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/pounds"
        app:layout_constraintBottom_toTopOf="@id/textViewCurrency"
        app:layout_constraintHorizontal_bias="0.495"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textViewCurrency"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/ENTER_CURRENCY"
        app:layout_constraintBottom_toTopOf="@id/buttonToConvert"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageViewMoney" />

    <EditText
        android:id="@+id/userEditTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/ENTER_CURRENCY_VALUE"
        app:layout_constraintTop_toBottomOf="@+id/textViewCurrency"
        app:layout_constraintBottom_toTopOf="@id/buttonToConvert"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        />

    <Button
        android:id="@+id/buttonToConvert"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/CONVERT"
        android:onClick="convertToDollarsOnButtonClick"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/textViewCurrency" />

```
<h2 align="center">UI</h2>

![11](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/Screen%20Shot%202021-04-16%20at%2011.03.14%20PM.png)

<h2 align="center">Java</h2>

This is the onClick function we covered

```
 public void convertToDollarsOnButtonClick(View view) {
        EditText userText = (EditText) (findViewById(R.id.userEditTextView));
        ImageView imageView = (ImageView) (findViewById(R.id.imageViewMoney));

        Log.i("button clicked", "User Entry");

        Toast.makeText(this, userText.getText().toString() + "£ is " + convertPoundsToDollars(Double.parseDouble(userText.getText().toString())) + "$", Toast.LENGTH_LONG).show();

        imageView.setImageResource(R.drawable.money);

    }
```

The function that's doing the converting 

```
private double convertPoundsToDollars(Double pounds) {
        double dollarInPounds = 1.38;
        return pounds * dollarInPounds;
    }
```

<h2 align="center">OUTPUT</h2>

![12](https://github.com/RamziJabali/Learning_Android/blob/main/screenshots/currencyConverter.gif)

<h1 align="center">Kotlin</h1>

<h2 align="center">Unit</h2>

`Unit` in Kotlin corresponds to the void in Java. Like void, `Unit` is the return type of any function that does not return any meaningful value, and it is optional to mention the `Unit` as the return type. But unlike void, `Unit` is a real class (Singleton) with only one instance.Aug 25, 2017


<h2 align="center">Print</h2>

In Kotlin the exection of the instructions begin with the `main` method.

```
fun main(){
   println("Hello world!")
}
```

Similar to Java Kotlin uses the keyword `print` and `println` to print is arguments to the output.

```
fun main(){ 
   print("Hello")
   println(" people!")
   print(2021)// Adds a line so that the text appears on the next line
}
```

<h2 align="center">Functions</h2>

Calling member functions uses the dot notation:

`Stream().read() // create instance of class Stream and call read()`

The function below has two parameters of type `Int` and has a return type of `Int` as well.

```
fun sum(a: Int, b: Int): Int {
    return a + b
}
```

A function body can be an expression. Its return type is inferred. Like so:

```
fun sum(a: Int, b: Int) = a + b

fun main() {
    println("sum of 19 and 23 is ${sum(19, 23)}")
}

//OutPut
//sum of 19 and 23 is 42
```

You can also make functions that do not return any value

```
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}
```

```
fun printMessage(message: String): Unit {                               // 1
    println(message)
}

fun printMessageWithPrefix(message: String, prefix: String = "Info") {  // 2
    println("[$prefix] $message")
}

fun sum(x: Int, y: Int): Int {                                          // 3
    return x + y
}

fun multiply(x: Int, y: Int) = x * y                                    // 4

fun main() {
    printMessage("What's up")                                               // 5                    
    printMessageWithPrefix("Hello", "Log")                              // 6
    printMessageWithPrefix("Hello")                                     // 7
    printMessageWithPrefix(prefix = "Log", message = "Hello")           // 8
    println(sum(1, 2))                                                  // 9
    println(multiply(2, 4))                                             // 10
}

/*
OutPut:
What's up
[Log] Hello
[Info] Hello
[Log] Hello
3
8
```
1) A simple function that takes a parameter of type `String` and returns `Unit` (i.e., no return value).
2) A function that takes a second optional parameter with default value `Info`. The return type is omitted, meaning that it's actually `Unit`.
3) A function that returns an integer.
4) A single-expression function that returns an integer (inferred).
5) Calls the first function with the argument `Hello`.
6) Calls the function with two parameters, passing values for both of them.
7) Calls the same function omitting the second one. The default value `Info` is used.
8) Calls the same function using named arguments and changing the order of the arguments.
9)Prints the result of the `sum` function call.
10) Prints the result of the `multiply` function call.


<h3 align="center">Infix Functions</h3>

What is infix function?

A function marked with the `infix` keyword can also be called using the infix notation (omitting the dot and the parentheses for teh call). Infix functions must meet the following requirements.

1) Member functions and extensions with a single parameter can be turned into infix functions.
2) They must have single parameter
3) The parameter must not accept variable number of arguments and must have no default value

```
infix fun Int.shl(x: Int): Int { ... }

// calling the function using the infix notation
1 shl 2

// is the same as
1.shl(2)
```

```
fun main() {  
  infix fun Int.times(str: String) = str.repeat(this)        // 1
  println(2 times "Bye ")//OUTPUT: Bye Bye                   // 2

  val pair = "Ferrari" to "Katrina"                          // 3
  println(pair) // OUTPUT: (Ferrari, Katrina) 
  
  infix fun Int.plus(number: Int) = number + this
  println(1 plus 2) // 3
  
  infix fun String.onto(other: String) = Pair(this, other)   // 4
  val myPair = "McLaren" onto "Lucas"
  println(myPair)
  
  val sophia = Person("Sophia")
  val claudia = Person("Claudia")
  sophia likes claudia                                       // 5
}
  class Person(val name: String) {
  val likedPeople = mutableListOf<Person>()
  infix fun likes(other: Person) { likedPeople.add(other) }  // 6
}
```

1) Defines an infix extension function on `Int`.
2) Calls the `infix` function.
3) Creates a `Pair` by calling the infix function `to` from the standard library.
4) Here's your own implementation of  `to` creatively called `onto`.
5) Infix notation also works on members functions (methods).
6) The containing class becomes the first parameter.

<h3 align="center">Operator Functions</h3>

Certain functions can be "upgraded" to operators, allowing their calls with the corresponding operator symbol.

```
    operator fun Int.times(str: String) = str.repeat(this)       // 1
    println(2 * "Bye ")                                          // 2
    //Bye Bye 
    
    operator fun String.get(range: IntRange) = substring(range)  // 3
    val str = "Always forgive your enemies; nothing annoys them so much."
    println(str[0..14])//says display from element 0 -> 14
    //Always forgive // it's the number of characters to display 
```
1) This takes the infix function from above one step further using the `operator` modifier.
2) The operator symbol for `times()` is `*` so that you can call the function using `2 * "Bye"`.
3) An operator function allows easy range access on strings.
4) The `get()` operator enables bracket-access syntax.


<h3 align ="center">Functions with `vararg` Parameters</h3>



<h2 align="center">Variables</h2>

Read-only local variables are defined using the keyword `val`. They can be assigned a value only once. 
Which is like Java's `final` keyword.

```
val a: Int = 1  // immediate assignment
val b = 2   // `Int` type is inferred
val c: Int  // Type required when no initializer is provided
c = 3       // deferred assignment
```
Variables that can be reassigned use the `var` keyword.

```
var x = 5 // `Int` type is inferred
x += 1
```

You can declare variables globaly as well.

```
val PI = 3.14
var x = 0

fun incrementX() { 
    x += 1 
}
```

<h2 align="center">Creating Classes and Instances</h2>

The keyword `class` is used to define a class like Java.

`class House` 

The properties of a class can be listed within it's declaration or body.

```
class Rectangle(var height: Double, var length: Double) {
    var perimeter = (height + length) * 2
}
```

The default constructor with parameters listed in the class declaration is available automatically.

```
class Rectangle(var height: Double, var length: Double) {
    var perimeter = (height + length) * 2 
}

fun main() {
    val rectangle = Rectangle(5.0, 2.0)
    println("The perimeter is ${rectangle.perimeter}")
}

//The perimeter is 14.0
```

Inheritance between classes is declared by a colon (`:`). 
Classes are final by default; to make a class inheritable, mark it as `open`.

```
open class Shape

class Rectangle(var height: Double, var length: Double): Shape() {
    var perimeter = (height + length) * 2
}
```

<h2 align="center">String Templates</h2>

```
var a = 1
// simple name in template:
val s1 = "a is $a" 

a = 2
// arbitrary expression in template:
val s2 = "${s1.replace("is", "was")}, but now is $a"

//a was 1, but now is 2
```
<h2 align="center">Conditional Expressions</h2>

<h3 align="center">If statement</h3>

```
fun maxOf(a: Int, b: Int): Int {
    if (a > b) {
        return a
    } else {
        return b
    }
}
```

In Kotlin, `if` can also be used as an expression.

```
fun maxOf(a: Int, b: Int) = if (a > b) a else b

// As expression
val max = if (a > b) a else b
```

Branches of if branches can be blocks. In this case, the last expression is the value of a block:

```
val max = if (a > b) {
    print("Choose a")
    a
} else {
    print("Choose b")
    b
}
```

If you're using `if` as an expression, for example, for returning its value or assigning it to a variable, the else branch is mandatory.


<h3 align="center">When expression</h3>

when defines a conditional expression with multiple branches.
It is similar to the switch statement in C-like languages. 
Its simple form looks like this.
```
fun describe(obj: Any): String =
    when (obj) {
        1          -> "One"
        "Hello"    -> "Greeting"
        is Long    -> "Long"
        !is String -> "Not a string"
        else       -> "Unknown"
    }
```

```
when (x) {
    1 -> print("x == 1")
    2 -> print("x == 2")
    else -> { // Note the block
        print("x is neither 1 nor 2")
    }
}
```

`when`matches its argument against all branches sequentially until some branch condition is satisfied.

`when` can be used either as an expression or as a statement. If it is used as an expression, the value of the first matching branch becomes the value of the overall expression. If it is used as a statement, the values of individual branches are ignored. 

The `else` branch is evaluated if none of the other branch conditions are satisfied. 
If `when` is used as an expression, the `else` branch is mandatory, unless the compiler can prove that all possible cases are covered with branch conditions, for example, with `enum` class entries and sealed class subtypes).

The way to define a common behavior for multiple cases is by using a comma `,` that allows you to combine the cases in a single line.

```
when(x){
 0, 1 -> print ("x == 0 or x ==1")
 else -> print ("otherwise")
}
```

You can use arbitrary expressions (not only constants) as branch conditions

```
when (x) {
    parseInt(s) -> print("s encodes x")
    else -> print("s does not encode x")
}
```

You can also check a value for being in or !in a range or a collection:

```
when (x) {
    in 1..10 -> print("x is in the range")
    in validNumbers -> print("x is valid")
    !in 10..20 -> print("x is outside the range")
    else -> print("none of the above")
}
```

Another option is checking that a value is or !is of a particular type. 

```
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
}
```

`when` can also be used as a replacement for an `if`-`else` `if` chain. If no argument is supplied, the branch conditions are simply boolean expressions, and a branch is executed when its condition is true:

```
when {
    x.isOdd() -> print("x is odd")
    y.isEven() -> print("y is even")
    else -> print("x+y is odd")
}
```


```
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("prefix")
    else -> false
}
```

<h3 align="center">For Loop</h3>

The syntax for the For Loop

```
for(item in colection) print(item)
```

The body of a `for` can be a block

```
for (item: Int in ints){
 //block of code
}
```

As mentioned before, for iterates through anything that provides an iterator.

This means that it:

has a member or an extension function `iterator()` that returns `Iterator<>`:

has a member or an extension function `next()`

has a member or an extension function `hasNext()` that returns `Boolean`.

All of these three functions need to be marked as `operator`.

To iterate over a range of numbers, use a range expression:

```
for (i in 1..3) {
        println(i)
    }
    for (i in 6 downTo 0 step 2) {
        println(i)
    }
```

```
val items = listOf("apple", "banana", "kiwifruit")
    for (item in items) {
        println(item)
     }
//or

val items = listOf("apple", "banana", "kiwifruit")
for (index in items.indices) {
    println("item at $index is ${items[index]}")
}
```

A `for` loop over a range or an array is compiled to an index-based loop that does not create an iterator object.

If you want to iterate through an array or a list with an index, you can do it this way:

```
for (i in array.indices) {
    println(array[i])
}
```
Alternatively, you can use the `withIndex` library function:

```
fun main() {
    val array = arrayOf("a", "b", "c")
    for ((index, value) in array.withIndex()) {
        println("the element at $index is $value")
    }
}
```



<h3 align="center">While Loop</h3>

while and do-while loops execute their body continuously while their condition is satisfied. The difference between them is the condition checking time:

while checks the condition and, if it's satisfied, executes the body and then returns to the condition check.

do-while executes the body and then checks the condition. If it's satisfied, the loop repeats. So, the body of do-while executes at least once regardless of the condition.

```
val items = listOf("apple", "banana", "kiwifruit")
var index = 0
while (index < items.size) {
    println("item at $index is ${items[index]}")
    index++
}
```

```
while (x > 0) {
    x--
}

do {
    val y = retrieveData()
} while (y != null) // y is visible here!
```
<h2 align="center">Ranges</h2>

Check if a number is within a range using the `in` operator.

```
val x = 10
val y = 9
if (x in 1..y+1) {
    println("fits in range")
}
```
Check if a number is out of range.

you can do NOT in as a means to check if something is out of range:

`!in`

```
val list = listOf("a", "b", "c")

if (-1 !in 0..list.lastIndex) {
    println("-1 is out of range")
}
if (list.size !in list.indices) {
    println("list size is out of valid list indices range, too")
}
```

Iterate over a range.

```
for (x in 1..5) {
    print(x)
}
```

Or over a progression.

```
for (x in 1..10 step 2) {
    print(x)
}

println()

for (x in 9 downTo 0 step 3) {
    print(x)
}
```

<h2 align="center">Collections</h2>

How to iterate over a collection

```
val items = listOf("apple", "banana", "kiwifruit")

for(item in items){
println(item)
}
```

How to check if a collection contains an object using the `in` operator

```
when {
    "orange" in items -> println("juicy")
    "apple" in items -> println("apple is also juicy")
}
```

Using lambda expressions to filter and map collections:

```
fun main() {
    val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
    fruits
        .filter { it.startsWith("a") }
        .sortedBy { it }
        .map { it.uppercase() }
        .forEach { println(it) }
}
```

<h2 align="center">Nullable values and null checks</h2>

A reference must be explicitly marked as nullable when `null` value is possible. Nullable type names have `?` at the end.

Return `null` if `str` does not hold an integer:

```
fun parseInt(Str: String): Int?{

}
```

Use a function returning nullable value:

```
fun printProduct(arg1: String, arg2: String) {
    val x = parseInt(arg1)
    val y = parseInt(arg2)

    // Using `x * y` yields error because they may hold nulls.
    if (x != null && y != null) {
        // x and y are automatically cast to non-nullable after null check
        println(x * y)
    }
    else {
        println("'$arg1' or '$arg2' is not a number")
    }    
}
```

or

```
if (x == null) {
    println("Wrong number format in arg1: '$arg1'")
    return
}
if (y == null) {
    println("Wrong number format in arg2: '$arg2'")
    return
}

// x and y are automatically cast to non-nullable after null check
println(x * y)
```

<h2 align="center">Type checks and automatic casts</h2>

The `is` operator checks if an expression is an instance of a type. If an immutable local variable or property is checked for a specific type, there's no need to cast it explicitly:

```
fun getStringLength(obj: Any): Int? {
    if (obj is String) {
        // `obj` is automatically cast to `String` in this branch
        return obj.length
    }

    // `obj` is still of type `Any` outside of the type-checked branch
    return null
}
```

or 

```
fun getStringLength(obj: Any): Int? {
    if (obj !is String) return null

    // `obj` is automatically cast to `String` in this branch
    return obj.length
}
```

or 

```
fun getStringLength(obj: Any): Int? {
    // `obj` is automatically cast to `String` on the right-hand side of `&&`
    if (obj is String && obj.length > 0) {
        return obj.length
    }

    return null
}
```

<h2 align="center">Basic types in Kotlin</h2>

<h2 align="center">Arrays</h2>

Different ways to define and initialize an array in Kotlin

```
    var x: IntArray = intArrayOf(1, 2, 3) // [1, 2, 3]
    var y = IntArray(5) //has a size of 5, but all elements are 0
    
    //[42, 42, 42, 42, 42]
    val arr = IntArray(5) { 42 } // has a size of 5 with all elements of value 42

    // e.g. initialise the values in the array using a lambda
    // Array of int of size 5 with values [0, 1, 2, 3, 4] (values initialised to their index value)
    var arr2 = IntArray(5) { it * 2 }
```
https://kotlinlang.org/docs/basic-types.html#numbers




