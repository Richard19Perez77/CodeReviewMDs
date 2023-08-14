String

`assocteWith` Returns a Map where keys are characters from the given char sequence and values are produced by the valueSelector function applied to each character.
```
val string = "bonne journée"
// associate each character with its code
val result = string.associateWith { char -> char.code }
// notice each letter occurs only once
println(result) // {b=98, o=111, n=110, e=101,  =32, j=106, u=117, r=114, é=233}
```

`associateBy` returns a map of values from transform
```
val charCodes = intArrayOf(72, 69, 76, 76, 79)
val byChar = charCodes.associateBy { Char(it) }
// L=76 only occurs once because only the last pair with the same key gets added
println(byChar) // {H=72, E=69, L=76, O=79}
```
