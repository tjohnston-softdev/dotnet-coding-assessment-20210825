### Question 3 - What is the time complexity of the `DetermineOneHitWonders` method?

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class OneHitWonders
{        
    public static List<Song> DetermineOneHitWonders(List<Song> songs)
    {
        List<Song> oneHitWonders = new List<Song>();
        foreach (Song song in songs)
        {
            bool oneHit = true;
            foreach (Song otherSong in songs)
            {
                if (otherSong.Id != song.Id && otherSong.Artist == song.Artist) oneHit = false;
            }
            if (oneHit) oneHitWonders.Add(song);
        }
        return oneHitWonders;
    }
}

public class Song
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Artist { get; set; }
}
```

\
**Answer:** O(songCount^2) - Quadratic

---

### Question 4 - Change the implementation of `DetermineOneHitWonders` to improve the time complexity.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class OneHitWonders
{        
    public static IEnumerable<Song> DetermineOneHitWonders(List<Song> songList)
    {
        // LINQ Query.
        IEnumerable<Song> oneHitWonders =
        from indSong in songList
        group indSong by indSong.Artist into artistSongs
        where artistSongs.Count() == 1
        select artistSongs.First();
        
        return oneHitWonders;
    }
}

public class Song
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Artist { get; set; }
}
```

\
**What is the time complexity of your implementation?**  
'O(log songCount) - Logarithmic'  
OR  
'O(artistCount) - Linear'

---

**Previous:** [Question 2](./question2.md)  
**Next:** [Question 5](./question5.md)

[Return to Index](../readme.md)