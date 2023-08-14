String

val string = "bonne journée"
// associate each character with its code
val result = string.associateWith { char -> char.code }
// notice each letter occurs only once
println(result) // {b=98, o=111, n=110, e=101,  =32, j=106, u=117, r=114, é=233}
