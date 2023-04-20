# Lab-8_202001218 #

<b> Software Engineering IT314 </b><br>
---------------------------------------------------------- <br>
<b>Name:</b> Vipulkumar Balubhai Ninama <br>
<b>Student ID:</b> 202001218 <br>
<b>Date: </b> 20/04/2023 <br>
<b>Lab </b> -8 <br>

-> <b> Goal: </b> The goal of this lab is to learn how to use JUnit to write unit tests for Java programs. <br>
-><b> Preliminary </b>– Learn about JUnit in Eclipse:
The primary goal of unit testing is to take the smallest piece of testable software in an application, isolate it from the remainder of the code, and determine whether or not it behaves the way you expect it to behave. Each unit is tested separately before integrating it into the rest of the program. In other words, classes should be tested in isolation from other classes (test the methods of a class before you use the class elsewhere). Unit testing has proven its value in that a large percentage of defects are identified during unit testing.

# Unit Testing with JUnit #

<b> Provided code: </b>

package JUnit; <br>
public class Boa { <br>
private String name; <br>
private int length; // the length of the boa, in feet <br>
private String favoriteFood; <br>
public Boa (String name, int length, String favoriteFood){ <br>
this.name = name; <br>
this.length = length; <br>
this.favoriteFood = favoriteFood; <br>
}  <br>
// returns true if this boa constrictor is healthy <br>
public boolean isHealthy(){ <br>
return this.favoriteFood.equals("granola bars"); <br>
} <br>
// returns true if the length of this boa constrictor is <br>
// less than the given cage length <br>
public boolean fitsInCage(int cageLength){ <br>
return this.length < cageLength; <br>
} <br>

public int lengthInInches(){ <br>
return this.length*12; <br>
// you need to write the body of this method <br>
} <br>
} <br>

<b> Lab Exercise: </b> <br>

1. Create a new Eclipse project, and within the project create a package. <br>
2. Create a class for a Boa. Here’s the code you can use (you may copy/paste): <br>
3. Follow the instructions in the JUnit tutorial in the section “Creating a JUnit Test Case in Eclipse”. You’ll be creating a test case for the class Boa. When you’re asked to select test method stubs, select both isHealthy() and fitsInCage(int). <br>



<b> Code: </b>  <br>
@Test  <br>
public void test() { <br>
Boa boa = new Boa("Benny",5,"granola bars"); <br>
assertTrue(boa.isHealthy()); <br>
} <br>
@Test  <br>
public void testIsHealthyWithFavoriteFoodNotGranolaBars() { 
Boa boa = new Boa("Benny", 5, "mice"); 
assertFalse(boa.isHealthy());  <br>
} <br>

@Test <br>
public void testFitsInCageWhenLengthLessThanCageLength() {  <br>
Boa boa = new Boa("Benny", 5, "granola bars");  <br>
assertTrue(boa.fitsInCage(10)); <br>
} <br>

@Test <br>
public void testFitsInCageWhenLengthGreaterThanCageLength() {  <br>
Boa boa = new Boa("Benny", 20, "granola bars");  <br>
assertFalse(boa.fitsInCage(10)); <br>
} <br>

4. Now it’s time to write some unit tests. Notice that the BoaTest class that JUnit created for you contains stubs for several methods. The first stub (for the method setUp()) is annotated with @Before. The @Before annotation denotes that the method setUp() will be run prior to the execution of each test method. setUp() is typically used to initialize data needed by each test. Modify the setUp() method so that it creates a couple of Boa objects, as follows:

@Before  <br>
public void setUp() throws Exception {  <br>
jen = new Boa("Jennifer", 2, "grapes");  <br>
ken = new Boa ("Kenneth", 3, "granola bars");  <br>
}  <br>

(You will need to add private fields for jen and ben to the BoaTest class, otherwise the compiler will complain that there are no variables with those names.)  <br>

<b> Code: </b>  <br>
private Boa jen;  <br>
private Boa ken;   <br>
@Before  <br>
public void setUp() throws Exception {   <br>
jen = new Boa("Jennifer", 2, "grapes");  <br>
ken = new Boa ("Kenneth", 3, "granola bars");  <br>
}   <br>

5. JUnit also provided stubs for two test methods, each annotated with @Test. Work on the testIsHealthy() method first. The purpose of this method is to check that the isHealthy() method in the Boa class behaves the way it’s supposed to. In the JUnit tutorial, read the section on “Writing Tests”. Modify the testIsHealthy() method so that it checks the results of activating the isHealthy() method on the two Boa objects you created in setup().
Likewise, modify the testFitsInCage() method to test the results of that method. Make sure your test is robust; it should check the results when the cage length is less than the length of the boa, when the cage length is equal to the length of the boa, and when the cage length is greater than the length of the boa. Should you write tests for both jen and ken?

6. Now you can run your tests. Read the section “Running Your Test Case” in the tutorial. Did you get a green bar in the JUnit pane? If you got a red bar, use the output in the JUnit pane to determine which test(s) failed. Fix your tests, and try running the test case again.
It’s important to note that a red bar doesn’t necessarily mean that the test case is written incorrectly; it could be that the method that’s being tested isn’t correct. In fact, that’s what unit testing is supposed to do – help us find errors in our code. When a test fails, you need to determine if the error is in the test case itself or in the code it’s testing.

<b> Code: </b>  <br>
@Test   <br>
public void testIsHealthy() {   <br>
Boa jen = new Boa("Jen", 5, "granola bars");    <br>
Boa ken = new Boa("Ken", 6, "mice");   <br>
assertTrue(jen.isHealthy());   <br>
assertFalse(ken.isHealthy());  <br>
}  <br>
@Test  <br>
public void testFitsInCage() {  <br>
Boa jen = new Boa("Jen", 5, "granola bars");   <br>
Boa ken = new Boa("Ken", 6, "mice");  <br>
assertTrue(jen.fitsInCage(6));  <br>
assertTrue(jen.fitsInCage(5));  <br>
assertFalse(jen.fitsInCage(4));  <br> 
assertTrue(ken.fitsInCage(7));  <br>
assertTrue(ken.fitsInCage(6));  <br>
assertFalse(ken.fitsInCage(5));  <br>
}  <br>

* Add a new method to the Boa class, with this purpose and signature:  <br>

// produces the length of the Boa in inches public int lengthInInches(){  <br>
// you need to write the body of this method  <br>
}  <br>
Add a new test case to the BoaTest class that tests the lengthInInches() method. Make sure you annotate the new test method with @Test. Run your tests.  <br>

* <b>Added Function: </b> <br>

public int lengthInInches(){  <br>
return this.length*12;  <br>
// you need to write the body of this method  <br>
}  <br>

<b> Test cases for this function: </b>  <br>
@Test  <br>
public void testLengthInInches() {  <br>
Boa boa = new Boa("John", 5, "grapes");   <br>
int expectedLengthInInches = 60;  <br>
int actualLengthInInches = boa.lengthInInches();  <br>
assertEquals(expectedLengthInInches, actualLengthInInches);  <br>
}  <br>



