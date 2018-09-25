---
layout: post
title:  "Android Basics - How to use Timer to show splash screen?"
date:   2018-09-23 10:00:00
categories: CodeSnippet
tags: Android Kotlin Timer
comments: true
logo: android
---

Here, I've created an example of a splash creen just like `LaunchScreen.storyboard` for iOS.
It stays on screen for 3 seconds & it shows login screen. One can refer following example to implement similar spash screen in his/her/their android application.

```kotlin
// 1. to import java utlilities
import java.util.*
// 2. to import timer tasks
import kotlin.concurrent.timerTask

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        
        // 3. Create timer
        val timer = Timer()
        
        // 4. Schedule timer. TimerTask is to call function nextTapped.
        // It will execute that block after 3 seconds.
        timer.schedule(timerTask{ nextTapped() }, 3000)
    }

    // 5. after 3 seconds, app will launch login screen
    fun nextTapped() {
        // 6. Start login screen.
        val intent = Intent(this, LoginActivity::class.java)
        startActivity(intent)
        // 7. Finish this activity so that when user presses back button, 
        // this screen won't appear.
        finish()
    }

}

```

![Demo Output for Android]({{"assets/2018-09-24/loginAnimation.gif" | absolute_url}})
