`List` operations

`Zip` takes two lists and combines them, it Returns a list of pairs built from 
the elements of this array and the other array with the same index. 
The returned list has length of the shortest collection.


```
val listA = listOf("a", "b", "c")
val listB = listOf(1, 2, 3, 4)
println(listA zip listB) // [(a, 1), (b, 2), (c, 3)]
```
```
val listA = listOf("a", "b", "c")
val listB = listOf(1, 2, 3, 4)
val result = listA.zip(listB) { a, b -> "$a$b" }
println(result) // [a1, b2, c3]
```
