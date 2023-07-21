Android Kotlin Extension Functions

Use `Glide` for loading image to `ImageView`

```
fun ImageView.loadImageFromUrl(url: String) {
    Glide.with(context)
        .load(url)
        .into(this)
}

val imageView = findViewById<ImageView>(R.id.imageView)
val imageUrl = "https://example.com/image.jpg"
imageView.loadImageFromUrl(imageUrl)
```
