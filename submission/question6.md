### Question 6 - Implement the `IsAncestor` function so that it supports a family tree of arbitrary depth.

**Hint:** Keep it simple and use recursion.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public interface IPerson
{
    string Name { get; }
    IPerson Parent1 { get; }
    IPerson Parent2 { get; }
}

public static class Ancestry
{
    public static bool IsParent(IPerson possibleParent, IPerson person)
    {
        return person.Parent1 != null && person.Parent1 == possibleParent
            || person.Parent2 != null && person.Parent2 == possibleParent;
    }

    public static bool IsAncestor(IPerson possibleAncestor, IPerson person)
    {
        // TODO Implement me
    }
}
```

\
**Answer:**

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public interface IPerson
{
    string Name { get; }
    IPerson Parent1 { get; }
    IPerson Parent2 { get; }
}

public static class Ancestry
{
    public static bool IsParent(IPerson possibleParent, IPerson person)
    {
        return person.Parent1 != null && person.Parent1 == possibleParent
            || person.Parent2 != null && person.Parent2 == possibleParent;
    }

    public static bool IsAncestor(IPerson possibleAncestor, IPerson person)
    {
        bool directParent = IsParent(possibleAncestor, person);
        
        if (directParent == true)
        {
            // Ancestor found via parent.
            return true;
        }
        
        bool grandparent1 = false;
        bool grandparent2 = false;
        bool indirectParent = false;
        
        if (person.Parent1 != null)
        {
            // Recurse on Parent 1
            grandparent1 = IsAncestor(possibleAncestor, person.Parent1);
        }
        
        if (person.Parent2 != null)
        {
            // Recurse on parent 2
            grandparent2 = IsAncestor(possibleAncestor, person.Parent2);
        }
        
        if (grandparent1 == true || grandparent2 == true)
        {
            // Ancestor found via grandparents.
            indirectParent = true;
        }
        
        // Not found this time.
        return indirectParent;
        
    }
}
```

---

**Previous:** [Question 5](./question5.md)  
**Next:**

[Return to Index](../readme.md)