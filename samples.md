Kotlin Samples

List

`associateBy` returns a map of values from transform
```
val charCodes = intArrayOf(72, 69, 76, 76, 79)
val byChar = charCodes.associateBy { Char(it) }
// L=76 only occurs once because only the last pair with the same key gets added
println(byChar) // {H=72, E=69, L=76, O=79}
```
```
val charCodes = intArrayOf(65, 65, 66, 67, 68, 69)
val byUpperCase = charCodes.associateBy({ Char(it) }, { Char(it + 32) })
// A=a only occurs once because only the last pair with the same key gets added
println(byUpperCase) // {A=a, B=b, C=c, D=d, E=e}
```
```
data class Person(val firstName: String, val lastName: String) {
    override fun toString(): String = "$firstName $lastName"
}
val scientists = listOf(Person("Grace", "Hopper"), Person("Jacob", "Bernoulli"), Person("Johann", "Bernoulli"))
val byLastName = scientists.associateBy { it.lastName }
// Jacob Bernoulli does not occur in the map because only the last pair with the same key gets added
println(byLastName) // {Hopper=Grace Hopper, Bernoulli=Johann Bernoulli}
```

`binarySearch` Search for element or return place it should go in at `(-insertion point - 1)`
```
data class Box(val value: String)

val values = listOf("A", "ant", "binding", "Box", "cell")
val boxes = values.map { Box(it) }

val valueToFind = "box"
// `boxes` list is sorted according to the following comparison function
val index = boxes.binarySearch { String.CASE_INSENSITIVE_ORDER.compare(it.value, valueToFind) }

if (index >= 0) {
    println("Value at $index is ${boxes[index]}") // Value at 3 is Box(value=Box)
} else {
    println("Box with value=$valueToFind was not found")
}
```
```
val list = mutableListOf('a', 'b', 'c', 'd', 'e')
println(list.binarySearch('d')) // 3

list.remove('d')

val invertedInsertionPoint = list.binarySearch('d')
val actualInsertionPoint = -(invertedInsertionPoint + 1)
println(actualInsertionPoint) // 3

list.add(actualInsertionPoint, 'd')
println(list) // [a, b, c, d, e]
```
