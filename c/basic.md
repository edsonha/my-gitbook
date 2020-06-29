# Basic

C\# is the language 

.Net is what we use to execute the code on our computer

Static \(call directly\) Instance method \(create a instance\)

int y // declaration 

y = 5 // initialization 

int y = 5 // declaration + initialization

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
```

**Params**

```csharp
static double GetSumMore(int num1, int num2, params double[] nums)

GetSumMore( 1, 2, 3, 4) // num1 is 1, num2 is 2 and the rest is params (3,4)
```

**Array**

```csharp
int[] luckyNumbers = { 4,  7, 10 }					
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

**Inheritance**

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

**List, Dictionary**

```csharp
//Array with dynamic size use List
List <int> numbers = new List<int> ();

Dictionary<string, int> prices = new Dictionary<string, int> (5);

```

**Enum**

```csharp
enum Breed { Bulldog, Boxer, Chihuahua };		

class Dog : Animal		
{		
	public Breed breed;	
	public Dog(Breed _breed)	
	{	
		breed = _breed
	}		
}		

Dog spotty = new Dog(Breed.Bulldog / Breed.Boxed / Breed.Chihuahua)	
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

