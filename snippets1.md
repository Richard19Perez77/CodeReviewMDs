`joinTo` appends the string from elements separated with separator and using a given prefix and postfix, use a limit for large collections, this will be followed by ... the truncated string remainder
```
val sb = StringBuilder("An existing string and a list: ")
val numbers = listOf(1, 2, 3)
println(numbers.joinTo(sb, prefix = "[", postfix = "]").toString()) // An existing string and a list: [1, 2, 3]

val lotOfNumbers: Iterable<Int> = 1..100
val firstNumbers = StringBuilder("First five numbers: ")
println(lotOfNumbers.joinTo(firstNumbers, limit = 5).toString()) // First five numbers: 1, 2, 3, 4, 5, ...
```

`map` returns a list of the results after a transform to each element
```
val numbers = listOf(1, 2, 3)
println(numbers.map { it * it }) // [1, 4, 9]

val peopleToAge = mapOf("Alice" to 20, "Bob" to 21)
println(peopleToAge.map { (name, age) -> "$name is $age years old" }) // [Alice is 20 years old, Bob is 21 years old]
println(peopleToAge.map { it.value }) // [20, 21]
```
`minus` can be used to remove a list from a list
```
fun main() {
    // Sample list of integers
    val originalList = listOf(1, 2, 3, 4, 5)

    // Elements to be removed
    val elementsToRemove = listOf(2, 4)

    // Create a new list without the elements specified to be removed
    val modifiedList = originalList.minus(elementsToRemove)

    println("Original list: $originalList")
    println("Modified list: $modifiedList")
}

Original list: [1, 2, 3, 4, 5]
Modified list: [1, 3, 5]
```

`none` is used to check for items in a list and returns true or false
```
val emptyList = emptyList<Int>()
println("emptyList.none() is ${emptyList.none()}") // true
​
val nonEmptyList = listOf("one", "two", "three")
println("nonEmptyList.none() is ${nonEmptyList.none()}") // false
emptyList.none() is true
nonEmptyList.none() is false

val isEven: (Int) -> Boolean = { it % 2 == 0 }
val zeroToTen = 0..10
println("zeroToTen.none { isEven(it) } is ${zeroToTen.none { isEven(it) }}") // false
println("zeroToTen.none(isEven) is ${zeroToTen.none(isEven)}") // false

val odds = zeroToTen.map { it * 2 + 1 }
println("odds.none { isEven(it) } is ${odds.none { isEven(it) }}") // true

val emptyList = emptyList<Int>()
println("emptyList.none { true } is ${emptyList.none { true }}") // true

zeroToTen.none { isEven(it) } is false
zeroToTen.none(isEven) is false
odds.none { isEven(it) } is true
emptyList.none { true } is true
```

`filter` return a list that contains only the items matching the predicate
```
val numbers: List<Int> = listOf(1, 2, 3, 4, 5, 6, 7)
val evenNumbers = numbers.filter { it % 2 == 0 }
val notMultiplesOf3 = numbers.filterNot { number -> number % 3 == 0 }

println(evenNumbers) // [2, 4, 6]
println(notMultiplesOf3) // [1, 2, 4, 5, 7]
```
