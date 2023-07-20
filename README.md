# KotlinCodeSnippets
A list of Kotlin coding snippets

`to` is used to create a Pair from this and that
```
val map = mapOf(1 to "x", 2 to "y", -1 to "zz")
println(map) // {1=x, 2=y, -1=zz}
```

`chunked` splits colleciton into a list of lists of size
```
val words = "one two three four five six seven eight nine ten".split(' ')
val chunks = words.chunked(3)

println(chunks) // [[one, two, three], [four, five, six], [seven, eight, nine], [ten]]
```


