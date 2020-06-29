# Basic

C\# is the language 

.Net is what we use to execute the code on our computer

Static \(call directly\) Instance method \(create a instance\)

int y // declaration 

y = 5 // initialization 

int y = 5 // declaration + initialization

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

\*\*\*\*

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

