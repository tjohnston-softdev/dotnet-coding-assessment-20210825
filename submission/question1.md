### Question 1 - The following function should print the numbers 1-5 to the console, separated by spaces, but it has a bug. Find the bug and fix it.

```csharp
using System;
using System.Collections.Generic;

public class Numbers
{
    public static void Print()
    {
        List<int> numbers = new List<int>();
        for (int i = 0; i < 5; i++)
            numbers.Add(i);
        Console.WriteLine(string.Join(" ", numbers));
    }
}
```

\
**Answer:**

```csharp
using System;
using System.Collections.Generic;

public class Numbers
{
    public static void Print()
    {
        List<int> numbers = new List<int>();
        for (int i = 1; i <= 5; i++)
            numbers.Add(i);
        Console.WriteLine(string.Join(" ", numbers));
    }
}
```

---

**Previous:**  
**Next:** [Question 2](./question2.md)

[Return to Index](../readme.md)