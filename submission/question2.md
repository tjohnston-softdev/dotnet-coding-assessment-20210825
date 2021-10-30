### Question 2 - Implement the function below so it returns the largest of the three values passed in.

```csharp
using System;

public class HighestNumber
{
    public static int FindHighestNumber(int a, int b, int c)
    {
        // TODO Implement me
    }
}
```

\
**Answer:**

```csharp
using System;

public class HighestNumber
{
    public static int FindHighestNumber(int a, int b, int c)
    {
        int abLarger = Math.Max(a, b);
        int overallLargest = Math.Max(abLarger, c);
        return overallLargest;
    }
}
```

---

**Previous:** [Question 1](./question1.md)  
**Next:** [Questions 3-4](./questions3-4.md)

[Return to Index](../readme.md)