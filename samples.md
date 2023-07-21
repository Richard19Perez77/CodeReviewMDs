Kotlin Samples

List

`associateBy` 
```
val charCodes = intArrayOf(72, 69, 76, 76, 79)
val byChar = charCodes.associateBy { Char(it) }
// L=76 only occurs once because only the last pair with the same key gets added
println(byChar) // {H=72, E=69, L=76, O=79}
```
