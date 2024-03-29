# Basic

**Glossary**

```csharp
Private fields: 
Can only be accessed by methods in the class (via getter and setter) and 
they are not accessible by subclasses or instantiation.

Protected fields:
Can only be accessed by methods in the class and by subclasses.

Read-only fields:
Set at runtime at constructors and can't be changed.

Method overloading:
When you have different versions of method 

Method override:
when you replace a method

Generic can only store one type
Non generic can store many types
```

**TryGetValue**

```csharp
if (!xlRow.Cell(SchemesExcelColumn.Version).TryGetValue(out int version))
{
    version = 1;
}
// If successfull, you get version. If not, you get version = 1 as default
            
       
if (results.TryGetValue(conditionBankId, out var conditionTemplateDtos))
{
    conditionTemplateDtos.Add(conditionTemplateDto);
}
else
{
    results.Add(conditionBankId, 
    new List<ConditionTemplateDto> {conditionTemplateDto});
}
// If successful of retrieving the conditionBankId (key) in RESULTS,
// you out the list of conditionTemplateDtos and add the conditionTemplateDto
// If fail, you add the RESULTS with conditionBankId as key 
// and initiliaze the new list as value
```

**Verbatim String**

```csharp
// verbatim ignore \n
Console.WriteLine(@"you \n have no power here");
// good example is 
// Console.WriteLine(@"C:\User\Admin\Doc\Super Cool.png");
// without verbatim, it will escape due to \ and give error

Console.WriteLine("you \n have power here");
```

**Null**

```csharp
Data types by default cannot have a value of null. 
When null is needed, add question mark:

int? randNum = null;
```

**Casting**

```csharp
// If you want to cast from one type to another - conversion
long num1 = 1234;
int num2 = (int)num1;
 
Console.WriteLine("Orig : {0} Cast : {1}", num1.GetType(), num2.GetType());
//Int64 and Int32
```

**Pass by Value vs Pass by Reference**

```csharp
// By default values are passed into a method
// and not a reference to the variable passed
// Changes made to those values do not effect the variables outside of the method

// To pass by reference:
int num1 = 10;
int num2 = 20;
 
Console.WriteLine("Before Swap num1 : {0} num2 : {1}", num1, num2); // 10 and 20
Swap(ref num1, ref num2);
Console.WriteLine("After Swap num1 : {0} num2 : {1}", num1, num2);  // 20 and 10

public static void Swap(ref int num1, ref int num2)
{
  int temp = num1;
  num1 = num2;
  num2 = temp;
}



static void Main(string[] args)
{
	int a = 1;
	int b = a;

	Console.WriteLine(a); // 1
	Console.WriteLine(b); // 1
	
	a = 5;

	Console.WriteLine(a); // 5
	Console.WriteLine(b); // 1, not affected by the change

	Test(a);

	Console.WriteLine(a); // 5, not affected by the method
	Console.WriteLine(b); // 1

	int[] c = { 10 };
	int[] d = c;

	Console.WriteLine(c[0]); // 10
	Console.WriteLine(d[0]); // 10

	d[0] = 20;

	Console.WriteLine(c[0]); // 20 // affected by the change
	Console.WriteLine(d[0]); // 20
}
static void Test(int a)
{
	a = 100;
}
```

**Params Modifier**

```csharp
static double GetSumMore(int num1, int num2, params double[] nums)

GetSumMore( 1, 2, 3, 4) // num1 is 1, num2 is 2 and the rest is params (3,4)
```

**Array**

```csharp
int[] luckyNumbers = { 4,  7, 10 }
var employees = new[] { "Mike", "Paul", "Rick" };					
// Create array with values

string[] friends = new string[5];					
// Create array with empty values with length of 5

//Multi-Dimensional Array
int[ , ] numberGrid = { 	
	{1, 2 },
	{3, 4 },
	{5, 6 }
};	

int [ , ] = new int [2, 3]			
// Create 2D array - 2 row and 3 columns (elements)
```

**Exception Handler - Prevent program from exiting and handle the error**

```csharp
try {
  // Your code block
}					
catch (Exception e) {					
	Console.WriteLine (e.Message)				
}					
					
// OR
					
catch (FormatException e) {
  // Your code block to handle FormatException					
}					
catch (DivideByZeroException) {					
  // Your code block to handle DivideByZeroException										
}					
finally {					
  // Always get executed no matter what		
}
```

**Constructor**

```csharp
class Book					
{					
  public string title;					
  public string author;					
  public int pages;					
					
	// You can have many constructor inside a class, including empty constructor				
	public Book (string aTitle, string aAuthor, int aPages ) 
	{				
		title = aTitle;			
		author = aAuthor;			
		pages = aPages;			
	}
}


// constructor overloading - Use with caution as it clutter the code
class Customer
{
	public int Id;
	public string Name;
	public readonly List<Order> Orders = new List<Order>(); 
	// initilize customer with order list and readonly prevent re-initilization
	
	public Customer (int id)
	{
		this.Id = id;
	}
	
	public Customer(int id, string name) : this(id) // called constructor with id
	{
		this.Name = name
	}
}
```

**Getter and Setter**

```csharp
// Using getter as read-only property					
class Player 				
{				
  private int _heatlh = 100			
  public int health 			
	{			
		get 		
		{		
			return _health	
		}		
	}			
				
	public void Damage (int _dmg)			
	{			
		_health -= _dmg		
	}			
}				
				
Player tom = new Player();				
tom.Damage(10)               // OK
tom.health = 80              // Not OK as it is Read Only
Console.Writeline(tom.health)// Print 90



// Using setter to prevent invalid value in object creation				
class Movie					
{					
  public string title;					
  public string director;					
  private string rating;					
					
					
  public Movie (string aTitle, string aDirector, string aRating ) {					
	  title = aTitle;				
	  director = aDirector;				
	  Rating = aRating;				
  }					
					
  public string Rating {					
	 get { return rating; }				
	 set {				
	  if (value == "G" || value == "R" || value == "NR") {				
		  rating = value			
	  }	else {				
		  rating = "NR"			
	  }				
  }					
}			

// You can have the getters and setters likt this and also set the default value
public string Owner { get; set; } = "No Owner";				
```

**Static - Class Static Attribute and Static Method and Static Class**

```csharp
// Class static attribute is about the class and not the object. 
// So, static attribute is shared in all instances.							
class Song							
{							
  public string title;							
  public string artist;
  public static int songCount = 0;						
							
	public Song (string aTitle, string aArtist ) {						
		title = aTitle;					
		artist = aArtist;	
		songCount++					
	}						
	
	public int getSongCount( ) {						
		return songCount;					
	}						
}							
							
Song holiday = new Song ("Holiday", "Green Day", 200);
// Another way to create object
Song holiday = new Song () { title= "Holiday", artist = "Green Day" }							
							
Console.WriteLine(Song.songCount)					// 1		
Console.WriteLine(holiday.songCount )			// Not accessible		
Console.WriteLine(holiday.getSongCount()) // Onlt accesible through object method		
							
							
// Static Methods & Class													
							
static class usefulTools // Static Class means you cannot create an instance
{							
	public static void SayHi( string name )
	// without the word static, you need to create an object to access the method		
	{						
		ConsoleWriteLine("hi" + name)										
	}						
}							
							
UsefulTools.SayHi("Ben")					
// So you can just call it from the class without creating an object
```

**Inner Class**

```csharp
 // You can create inner classes that are normally helper classes for the outer 
 // class because it can access private members of the outer class
 class Animal {
   public class AnimalHealth {
     public bool HealthyWeight(double height, double weight) {
       double calc = height / weight;
       if ((calc >= .18) && (calc <= .27)) {
         return true;
       }
       else return false;
     }
   }
 }
 
Animal.AnimalHealth getHealth = new Animal.AnimalHealth();
 
Console.WriteLine("Is my animal healthy : {0}", getHealth.HealthyWeight(11, 46));
```

**Inheritance - Is-A relationship \(Dog Class is Animal Class\)**

```csharp
// Italian chef override method of normal chef
public override void MakeSpecialDish() {
  Console.WriteLine("Cook Spagethi");
}

// Normal chef method that can be overriden by sub-class
public virtual void  MakeSpecialDish ()	{		
  Console.WriteLine("Cook BBQ Ribs");
}
```

**Aggregation or Delegate - Has-A relationship \(Animal Class has a Animal Id Info Class\)**

```csharp
class Animal {
    protected AnimalIDInfo animalIDInfo = new AnimalIDInfo();
  
    public void SetAnimalIDInfo(int idNum, string owner) {
        animalIDInfo.IDNum = idNum;
        animalIDInfo.Owner = owner;
    }
}

class AnimalIDInfo {
    public int IDNum { get; set; } = 0;
    public string Owner { get; set; } = "No Owner";
}
```

**Polymorphism**

```csharp
class Animal {
  public void MakeSound() {
    Console.WriteLine($"{Name} says {Sound}");
}

// You can define 2 Animal objects but have one actually be a Dog type. 
Animal monkey = new Animal() { Name = "Happy", Sound = "Eeeeee" };
 
Animal spot = new Dog() { Name = "Spot", Sound = "Wooooff", Sound2 = "Geerrrr" };

spot.makeSound() // spot says Wooooff (without the sound2)

// With polymorphism with virtual and override
// This is an example of how Polymorphism allows a subclass to override a method
// in the super class and even if the subclass is defined as the super class
// type the correct method will be called
class Animal {
  public virtual void MakeSound() {
    Console.WriteLine($"{Name} says {Sound}");
}

class Dog : Animal {
  public override void MakeSound() {
    Console.WriteLine($"{Name} says {Sound} and {Sound2}");
  }
}

spot.makeSound() // spot says Wooooff and Geerrrr

// Another example of polymorphism
abstract class Shape {} // abstract is a clss that you don't want to instantiate

class Circle : Shape {}
class Rectangle : Shape {} 

Shape[] shapes = {new Circle(5), new Rectangle(4,5)};
foreach(Shape s in shapes) {
  Circle testCirc = s as Circle; // Use "as" to check if an object is of a specific type
  if(testCirc == null) {
    Console.WriteLine("This isn't a Circle");
  }
  if(s is Circle) { // Use "is" to check the data type
    Console.WriteLine("This isn't a Rectangle");
  }
}

```

**List, Dictionary, Tuple**

```csharp
// Array with dynamic size use List and it can only consist of one data type
List <int> numbers = new List<int> ();
number.Add(1); // OK
number.Add("Hello"); // Not OK

// Dictionary<TKey, TValue>
Dictionary<string, int> myDictionary = new Dictionary<string, int>();
myDictionary.Add("a", 100);
myDictionary.Add("b", 200);
Console.WriteLine(myDictionary["a"]); // 100

// Tuple, carry different type of data 
public Tuple<string, int> Math(int a, int b)
{
	string c = "Hello World";
	int d = a * b;
	return Tuple.Create(c, d);
}
static void Main(string[] args)
{
	Program p = new Program();
	var obj = p.Math(10, 20);
	Console.WriteLine(obj.Item1); // Hello World
	Console.WriteLine(obj.Item2); // 200
}

// New way to create tuple
public (string Hello, int Multiply) Math(int a, int b)
{
	string c = "Hello World";
	int d = a * b;
	return (c, d);
}
static void Main(string[] args)
{
	Program p = new Program();
	var obj = p.Math(10, 5);
	Console.WriteLine(obj.Hello);
	Console.WriteLine(obj.Multiply);
} 
```

**Enum**

```csharp
enum Breed { Bulldog, Boxer, Chihuahua };		

class Dog
{		
	public Breed breed;	
	public Dog(Breed _breed)	
	{	
		breed = _breed
	}		
}		

Dog spotty = new Dog(Breed.Bulldog / Breed.Boxer/ Breed.Chihuahua)
Console.WriteLine(spotty.breed);	


enum CarColor : byte // initialize to byte, the default is integer
{
  Orange = 1, // initialize to 1, the default is 0
  Blue,
  Green,
  Red,
  Yellow
}

static void Main(string[] args)
{
  CarColor car1 = CarColor.Yellow;
  PaintCar(car1);
}

static void PaintCar(CarColor cc)
{
  Console.WriteLine("The car was painted {0} with the code {1}",
  cc, (byte)cc);
}
```

**Interface**

Interface is like a contract... Why not use base class? Because you can derive from multiple interfaces

**Generics**

Handle unknown data types

```csharp
// Generic method inside non-generic class						
class Utility						
{						
	public static bool CompareValues<T01, T02> (T01 value1, T02 value2)					
	{					
		return value1.Equals(value2);				
	}					
	public static bool CompareTypes<T01, T02> (T01 type1, T02 type2)					
	{					
		return typeof(T01).Equals(typeof(T02));				
	}					
}						
						
Console.WriteLine(Utility.CompareValues(10, "Hello"));		 // FALSE
Console.WriteLine(Utility.CompareTypes("World", "Hello")); // TRUE
```

**Dependency Injection - Add Singleton, Add Scoped and Add Transient**

| **Service Type** | In the scope of a given HTTP request | Across different HTTP request |
| :--- | :--- | :--- |
| Scoped Service | Same Instance | New Instance |
| Singleton Service | Same Instance | Same Instance |
| Transient Service | New Instance | New Instance |

**Defensive Programming - Mosh**

```csharp
//Preventing the count greater than no of elements in the list or count is 0 of less than 0

if (count > list.Count || count <= 0)
{
    //first arguement is the parameter
    //second arguement is the message we want to show
    throw new ArgumentOutOfRangeException("count", "Count should be between 1 and the number of elements in the list");
}


//Preventing a null being thrown as the list
if (list == null)
{
    throw new ArgumentNullException("list");
}
```

Different type of access modifier: private, public, protected and internal. [`Link`](https://code-maze.com/csharp-basics-access-modifiers/)\`\`

