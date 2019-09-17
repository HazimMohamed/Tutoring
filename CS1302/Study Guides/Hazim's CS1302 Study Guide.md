<center> <h1> Hazim's CS1302 Study Guide</h1> </center>

<center> <h2> Test 1</h2> </center>

## Table of Contents

1. [FAQ](#faq)
2. [Unix Commands](#unix commands)
3. [](#third-example)
4. [Fourth Example](#fourth-examplehttpwwwfourthexamplecom)

## Who you? ##

I'm a tutor for CS1302. I took Cotterell's CS1302 class in Spring 2018 and I was a PLA ( an in-class TA ) for Cotterell/Barnes' CS1302 class for Spring 2019. So I'm basing most of my information

## What's the format of the test going to be like? ##

Although I can't guarentee the format of the test, both times I've seen it it's been the same. The first section will most likely be multiple choice with the mostly straight forward memorizable facts ( Which of the following is an unchecked exception?, Which of the following commands prints the contents of a file?, etc. ). The multiple choice section will probably be where you would use your cheat sheet the most. The following section will make up the bulk of the test 

## What type of material is going to be on the test? ##

Cotterell pulled heavily from class exercises and in-class-activities both times I was involved in his class. He covers all the material pretty thoroughly in his tests, but I would spend more time on concepts ( inheritance, polymorphism, etc. ) than I would on specifics ( which ). When I took the class I paid attention in class so I knew the concepts  and didn't use a cheat sheet and I aced the first exam. I would highly suggest supplementing this study guide

## How should I read this study guide? ##



## Unix Commands
Here are some of the most common Unix commands. It would be a good idea to familiarize yourself with them before the test, however I wouldn't dedicate too much time since you can always create a similar table on your cheat sheet.

<table>
	<tr>
		<th>Command</th>
		<th>What it does</th>
		<th>Important Flags</th>
	</tr>
	<tr> 
		<td> cd  &ltfolder in the current directory&gt </td> 
		<td> Changes your current directory to the specified folder </td>
		<td> N/A </td>
	 </tr>
	<tr> 
		<td> ls [folder in the current directory] </td> 
		<td> Lists all the contents of the current directory. If a directory is put after the ls command, displays the 		contents of that directory instead. By default this doesn't show any directory/file whose name starts with '.'</td>
		<td> 
			<li> <b>- a</b> : shows all files, including ones who start with '.'
			<li> 
		</td>
	 </tr>
	 	<tr> 
		<td> mkdir &ltfolder name that you want to create&gt </td> 
		<td> Creates a folder with the given name</td>
		<td> 
			<li> <b>-p:</b> Creates a series of folders all in one commands. For example mkdir -p src/cs1302/uga would create all three folders nested in one another.
		</td>
	 </tr>
 	<tr> 
		<td> rm &ltfile/folder in the current directory&gt </td> 
		<td> Changes your current directory to the specified folder </td>
		<td> N/A </td>
	 </tr>
	  	<tr> 
		<td> chmod &ltfile/folder in the current directory&gt &ltA number representing the new permissions></td> 
		<td> Changes your current directory to the specified folder </td>
		<td> N/A </td>
	 </tr>
	  	<tr> 
		<td> cat &ltfile in the current directory&gt </td> 
		<td> Changes your current directory to the specified folder </td>
		<td> N/A </td>
	 </tr>
	  	<tr> 
		<td> cd  &ltfolder in the current directory&gt </td> 
		<td> Changes your current directory to the specified folder </td>
		<td> N/A </td>
	 </tr>
</table>

## Permissions
Permissions just statements dictating who can interact with a file you've made and in which ways they can interact. A permission for a single user is basically three yes or no questions:

* Can this user read this file?
* Can this user write to this file?
* Can this user execute this file?

This is shortened to:
```
rwx
```
If a permission is not available for a user, it's replaced with a `-`. For example if I can read and write to a file, but not execute my permissions would be:
```
rw-
```

Unix allows you to set different permissions for three different groups of people: **user**, **group**, **other**. User is the person who made the file, group is anybody who is in the same group as the person whose made the file ( for example all undergrads, or all cs1302 students ) and other is everyone else.

A permission might look like this:
```
User can rwx
Group can r-x
Others can r--
```

This is shortened to:
```
rwx r-x r--
```
To convert this permission into a number you first replace any thing that's not a dash with 1 and anything that's a dash with 0. So ` rwx r-x r-- ` would be:
```
111 101 100
```
Then you would take each 3 digit group as its own binary number. If you don't know how to read binary numbers read <a target="_blank" href="">this</a>. `111` in binary is 7, `101` in binary is 5, and `100` in binary is 4. So our permission would end up being 754. Cotterell might quiz you on the __number format__ of  `754`. It's formatted as an __octal number__. Let's do one more, more quickly this time:
1. We want the user to be able to read, and write but not execute; the group to be able to read only; all others to be able to read only.
2. This is represented as `rw- r-- r--` 
3. Replace the letters with 1 and the dashes with 0 : `110 100 100`
4. `110` is 6; `100` is 4; `100` is 4
5. The octal number we're looking for is `644`

## Interfaces
Interfaces are a very important concept. Unlike a lot of the stuff that you learn in this unit, this won't go away. You'll use it in the rest of this class, in the rest of your computer science classes, and in your career. 

An interface is - on the most basic level - is a list of methods. When you say a class __implements__ an an interface it just means that that class has their own version of all the methods that are listed in the interface. That's why interfaces almost always end in "-able"; the interface lists things that an implementing class should be __able__ to do.

Lets look at the following interface:

```java
interface Combustable {
  
  public void catchFire();
  
  public void burnFor(int numberOfMinutes);
  
}
```

_Note that the methods don't have bodies. In other words the methods don't say how they have to be used. Every implementing class can write the `catchFire()` method differently. These type of methods without bodies are called_ __abstract methods__. 

And let's have a class here:

```java
public class Human {
  
  private String name;
  private int age;
  private boolean isMale;
  
  public void sayName() {
    System.out.println("Hello my name is " + this.name + "!");
  }
  
}
```

If we make our class implement the interface we are saying that a `Human` class has every method listed in the combustable interface. But the human does not get these methods automatically - obviously since the methods listed in `Combustable` don't have bodies. We have to manually write the methods of `Combustable` in `Human` if we say `Human implements Combustable`. So this:

```java
public class Human implements Combustable {
  
  private String name;
  private int age;
  private boolean isMale;
  
  public void sayName() {
    System.out.println("Hello my name is " + this.name + "!");
  }
  
}
```

would not compile. It would lead to this error:

```java
Human.java:1: error: Human is not abstract and does not override abstract method burnFor(int) in Combustable

```

This is the compiler telling us: " You said that `Human` has every method listed in `Combustable` but I found the method `burnFor(int)` that is in `Combustable` but not in `Human`. To fix this we write the methods for `Combustable` in `Human`.

```java
public class Human implements Combustable {
  
  private String name;
  private int age;
  private boolean isMale;
  
  public void sayName() {
   System.out.println("Hello my name is " + this.name + "!");
  }
  
  public void catchFire() {
    System.out.println("AHHHH! I'm burning!");
  }
  
  public void burnFor(int) {
    
  }
}
```

