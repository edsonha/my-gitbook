# Basic

**Accessing Object Argument**

```csharp
int result = num1 * num2 * num3;
Console.WriteLine("Output: {0} x {1} x {2} = {3}", num1, num2, num3, result);

// {0} is index 0 - num1
// {1} is index 1 - num2
// {2} is index 2 - num3
// {3} is index 3 - result
```

**Accessing Object Argument - as Operation**

```csharp
Console.WriteLine("{0} / {1} = {2}", num1, num2, num1/num2);
Console.WriteLine("{0} mod {1} = {2}", num1, num2, num1%num2);
```

**Remove element in string**

```csharp
Console.WriteLine(remove_char("w3resource", 1)); //wresource
Console.WriteLine(remove_char("w3resource", 9)); // w3resourc

public static string remove_char(string str, int n)
{
        return str.Remove(n, 1);
}
```

**Lowercase**

```csharp
Console.WriteLine(string.ToLower());
```

**Foreach and Split**

```csharp
string line = "Write a C# Program";
string[] words = line.Split(new[] { " " }, StringSplitOptions.None);

foreach (String s in words)
{
    Console.WriteLine(s);
}
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

**JS === C\#**

* Substring
* Switch statement
* Ternary Operator

