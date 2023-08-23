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

`distinct`
```
val list = listOf('a', 'A', 'b', 'B', 'A', 'a')
println(list.distinct()) // [a, A, b, B]
println(list.distinctBy { it.uppercaseChar() }) // [a, b]
```

`setOf` and `filter` to Remove vowels from a String
```
fun removeVowels(input: String): String {
    val vowels = setOf('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U')
    return input.filter { !vowels.contains(it) }
}

fun main() {
    val inputString = "Hello, World!"
    val result = removeVowels(inputString)
    println("Original: $inputString")
    println("Without vowels: $result")
}
```

`drop` to remove or remove with condition
```
val chars = ('a'..'z').toList()
println(chars.drop(23)) // [x, y, z]
println(chars.dropLast(23)) // [a, b, c]
println(chars.dropWhile { it < 'x' }) // [x, y, z]
println(chars.dropLastWhile { it > 'c' }) // [a, b, c]
```

`find` can find a first or last value based on condition
```
val numbers = listOf(1, 2, 3, 4, 5, 6, 7)
val firstOdd = numbers.find { it % 2 != 0 }
val lastEven = numbers.findLast { it % 2 == 0 }

println(firstOdd) // 1
println(lastEven) // 6
```

`flatMap` return a single list as result of transform
```
val list = listOf("123", "45")
println(list.flatMap { it.toList() }) // [1, 2, 3, 4, 5]
```
```
val map = mapOf("122" to 2, "3455" to 3)
println(map.flatMap { (key, value) -> key.take(value).toList() }) // [1, 2, 3, 4, 5]
```

`flatten` return a single list of all elements from all arrays in an array
```
val deepArray = arrayOf(
    arrayOf(1),
    arrayOf(2, 3),
    arrayOf(4, 5, 6)
)

println(deepArray.flatten()) // [1, 2, 3, 4, 5, 6]
```
```
val deepList = listOf(listOf(1), listOf(2, 3), listOf(4, 5, 6))
println(deepList.flatten()) // [1, 2, 3, 4, 5, 6]
```

`groupBy` use keySelector to return map of associations
```
val words = listOf("a", "abc", "ab", "def", "abcd")
val byLength = words.groupBy { it.length }

println(byLength.keys) // [1, 3, 2, 4]
println(byLength.values) // [[a], [abc, def], [ab], [abcd]]

val mutableByLength: MutableMap<Int, MutableList<String>> = words.groupByTo(mutableMapOf()) { it.length }
// same content as in byLength map, but the map is mutable
println("mutableByLength == byLength is ${mutableByLength == byLength}") // true
```
```
val nameToTeam = listOf("Alice" to "Marketing", "Bob" to "Sales", "Carol" to "Marketing")
val namesByTeam = nameToTeam.groupBy({ it.second }, { it.first })
println(namesByTeam) // {Marketing=[Alice, Carol], Sales=[Bob]}

val mutableNamesByTeam = nameToTeam.groupByTo(HashMap(), { it.second }, { it.first })
// same content as in namesByTeam map, but the map is mutable
println("mutableNamesByTeam == namesByTeam is ${mutableNamesByTeam == namesByTeam}") // true
```

`groupingBy` chain together a grouping with group and fold operations
```
val words = "one two three four five six seven eight nine ten".split(' ')
val frequenciesByFirstChar = words.groupingBy { it.first() }.eachCount()
println("Counting first letters:")
println(frequenciesByFirstChar) // {o=1, t=3, f=2, s=2, e=1, n=1}

val moreWords = "eleven twelve".split(' ')
val moreFrequencies = moreWords.groupingBy { it.first() }.eachCountTo(frequenciesByFirstChar.toMutableMap())
println(moreFrequencies) // {o=1, t=4, f=2, s=2, e=2, n=1}
```

`groupingBy` with `aggregate` from a `listOf` int
```
val numbers = listOf(3, 4, 5, 6, 7, 8, 9)

val aggregated = numbers.groupingBy { it % 3 }.aggregate { key, accumulator: StringBuilder?, element, first ->
    if (first) // first element
    StringBuilder().append(key).append(":").append(element)
    else
    accumulator!!.append("-").append(element)
}

println(aggregated.values) // [0:3-6-9, 1:4-7, 2:5-8]
```
