### Question 5 - The routine below searches the contents of a perfectly balanced binary tree.

```csharp
public Node FindInTree(Node node, Predicate<Node> findPredicate)
{
    return InnerFindInTree(node, findPredicate, 1);
}

private Node InnerFindInTree(Node node, Predicate<Node> findPredicate, int stackDepth)
{
    if (stackDepth > MaximumStackDepth)
        return null;
    if (node == null)
        return null;

    Node leftResult = InnerFindInTree(node.LeftChild, findPredicate, stackDepth + 1);
    Node rightResult = InnerFindInTree(node.RightChild, findPredicate, stackDepth + 1);
    
    if (findPredicate(node))
        return node;
    if (leftResult != null)
        return leftResult;
    if (rightResult != null)
        return rightResult;
    return null;
}
```

\
**If an upper limit of 100,000 nodes is assumed, what should the `MaximumStackDepth` constant be set to?**  
17: 100000 / (2^17) = 0.76

**If the binary tree is not balanced, what is at risk of occurring with the code above?**  
This code assumes that each given node has both Left and Right children nodes. This might be reasonable for a balanced tree. However, if the branching is uneven such as if a node only has a Left child, there will be runtime errors because of a null object.

**The code above has a major performance issue. What is it?**  
The 'findPredicate' check should be at the beginning of the function and not the end. Otherwise the search will go deeper than necessary. Recursion should be called after this check.

---

**Previous:** [Questions 3-4](./questions3-4.md)  
**Next:** [Question 6](./question6.md)

[Return to Index](../readme.md)