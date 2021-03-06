---
description: >-
  Generates a Decentralized Id Token which acts as a proof of authentication to
  resource servers.
---

# getIdToken

### **Public Methods**

| **Methods** |
| :--- |
| **getIdToken**\(configuration: GetIdTokenConfiguration?\): CompletableFuture&lt;GetIdTokenResponse&gt; |

### Returns

`GetIdTokenResponse: Response<String>()`

The `Completable` resolves with a true boolean value if update email is successful and rejects with a specific error code if the request fails. 

```kotlin
class MagicActivity: AppCompatActivity() {

    lateinit var magic: Magic
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        magic = Magic(this, "YOUR_PUBLISHABLE_KEY")
    }
    
    // ⭐️Assuming user is logged in 
    fun getIdToken(v: View) {
        val configuration = GetIdTokenConfiguration(lifespan = 900)
        val completable = magic.user.getIdToken(configuration)
        completable.whenComplete { response: GetIdTokenResponse?, error: Throwable? ->
            if (response != null) {
                Log.d("Magic", response.result)
            } else {
                // handle Error
            }
        }
    }
}
```

### Associated Class

`GetIdTokenConfiguration(lifespan: Long? = 900)`

* `lifespan?` : will set the lifespan of the generated token. Defaults to 900s \(15 mins\)

 

