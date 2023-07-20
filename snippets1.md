`joinTo` appends the string from elements separated with separator and using a given prefix and postfix, use a limit for large collections, this will be followed by ... the truncated string remainder
```
val sb = StringBuilder("An existing string and a list: ")
val numbers = listOf(1, 2, 3)
println(numbers.joinTo(sb, prefix = "[", postfix = "]").toString()) // An existing string and a list: [1, 2, 3]

val lotOfNumbers: Iterable<Int> = 1..100
val firstNumbers = StringBuilder("First five numbers: ")
println(lotOfNumbers.joinTo(firstNumbers, limit = 5).toString()) // First five numbers: 1, 2, 3, 4, 5, ...
```
