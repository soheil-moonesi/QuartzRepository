![[Pasted image 20241211170611.png]]

![[Pasted image 20241211170621.png]]

The Iterator Pattern is a design pattern that provides a way to access the elements of a collection object sequentially without exposing its underlying representation. In C#, this pattern can be implemented using `IEnumerable<T>` and `IEnumerator<T>` interfaces. Here’s a detailed explanation and example of implementing the Iterator Pattern in C#.

### Components of the Iterator Pattern

1. **Iterator Interface (`IEnumerator<T>`):**
    
    - Provides methods for traversing elements in the collection (e.g., `MoveNext`, `Current`, `Reset`).
2. **Aggregate Interface (`IEnumerable<T>`):**
    
    - Provides a method to create an iterator (e.g., `GetEnumerator`).
3. **Concrete Iterator:**
    
    - Implements the iterator interface to traverse the collection.
4. **Concrete Aggregate:**
    
    - Implements the aggregate interface to return an iterator.