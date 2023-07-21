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
