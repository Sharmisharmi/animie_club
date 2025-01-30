# 🎌 Anime Club 📱  

A modern Android application for anime lovers, built with **Kotlin**, **XML-based UI**, and **Retrofit** for API integration. Stay updated with the latest anime, and explore a world of anime content!  

## 🚀 Features 
- 📺 **Anime Trailers & Details**
- 🖌️ **XML-based UI for Flexible Design**
- 🎨 **Custom UI Components with Third-Party Libraries** 
- 🌍 **REST API Integration using Retrofit**

## 🛠️ Tech Stack  
- **Language:** Kotlin  
- **UI:** XML, Material Design  
- **Architecture:** MVVM + Repository Pattern  
- **Networking:** Retrofit
- **Video Streaming:** Android YouTube Player  
- **Custom UI Components:** Canvas, Material Components, Glide, and Picasso

## 🎨 Third-Party Libraries Used  
| Library | Purpose |  
|---------|---------|  
| [Retrofit](https://github.com/square/retrofit) | API calls |  
| [Glide](https://github.com/bumptech/glide) | Image loading |  
| [Android YouTube Player](https://github.com/PierfrancescoSoffritti/android-youtube-player) | Playing anime trailers |  
| [Material Components](https://material.io/develop/android) | Custom UI elements |  

## 📷 Screenshots  
<div style="display: flex; justify-content: center; align-items: center; padding: 90px;">
  <img src="https://github.com/Sharmisharmi/animie_club/blob/master/screen_shot_1.jpeg" width="35%" height="35%" style="margin-right: 20px;">
  <img src="https://github.com/Sharmisharmi/animie_club/blob/master/screen_shot_2.jpeg" width="35%" height="35%">
</div>






## 🔗 API Integration  
The app fetches anime data from a REST API using **Retrofit** and plays trailers using **Android YouTube Player**.  

### Example YouTube Player Integration  
```kotlin
val youTubePlayerView = findViewById<YouTubePlayerView>(R.id.youtube_player_view)
lifecycle.addObserver(youTubePlayerView)

youTubePlayerView.addYouTubePlayerListener(object : AbstractYouTubePlayerListener() {
    override fun onReady(youTubePlayer: YouTubePlayer) {
        youTubePlayer.loadVideo("VIDEO_ID", 0f) // Replace with actual video ID
    }
})
```
## 🌐 Example Retrofit API Call
```kotlin
interface AnimeApiService {
    @GET("anime")
    suspend fun getAnimeList(): Response<List<Anime>>
}

object RetrofitClient {
    private val retrofit = Retrofit.Builder()
        .baseUrl("https://api.example.com/") // Replace with actual API base URL
        .addConverterFactory(GsonConverterFactory.create())
        .build()

    val apiService: AnimeApiService = retrofit.create(AnimeApiService::class.java)
}
