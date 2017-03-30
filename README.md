[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ShelfView-brightgreen.svg?style=flat)](https://android-arsenal.com/details/1/5299) [![MaterialUp](https://img.shields.io/badge/MaterialUp-ShelfView-deepblue.svg?style=flat)](https://material.uplabs.com/posts/shelfview)


## ShelfView ##

*Android custom view to display books on shelf*

<img src="/portrait.png" width="340"> <img src="/landscape.png" width="528">




#### How to use ####
----

**build.gradle**
```
allprojects {
            repositories {
                maven {
                    url 'https://jitpack.io'
                }
            }
        }
```


```
dependencies {
	        compile 'com.github.tdscientist:ShelfView:v1.0'
	}
```

**Layout**
```
<com.tdscientist.shelfview.ShelfView 		  
    android:id="@+id/shelfView"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />

```


**Activity**
```
import com.tdscientist.shelfview.BookModel;
import com.tdscientist.shelfview.ShelfView;
import java.util.ArrayList;

public class MainActivity extends AppCompatActivity implements ShelfView.BookClickListener {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ShelfView shelfView = (ShelfView) findViewById(R.id.shelfView);
        shelfView.setOnBookClicked(this);
        ArrayList<BookModel> models = new ArrayList<>();

        models.add(new BookModel("http://eurodroid.com/pics/beginning_android_book.jpg", "1", "Beginning Android"));
       
 		shelfView.loadData(models, ShelfView.BOOK_SOURCE_URL);


    }

	@Override
    public void onBookClicked(int position, String bookId, String bookTitle) {	
    	// handle click events here 
        //Toast.makeText(this, bookTitle, Toast.LENGTH_SHORT).show();
    }
}

```



#### Loading book covers from other sources ####
----

* Internal/External directory in the device
```
model.add(new BookModel("/path/to/android_book_cover.jpg", "1", "Let's Talk About Android"));
shelfView.loadData(model, ShelfView.BOOK_SOURCE_FILE);
``` 



* Assets folder
```
model.add(new BookModel("android.jpg", "1", "Android for Experts"));
shelfView.loadData(model, ShelfView.BOOK_SOURCE_ASSETS_FOLDER);
```
 


* Drawable folder
```
model.add(new BookModel("alice", "1", "Alice in Wonderland"));
shelfView.loadData(model, ShelfView.BOOK_SOURCE_DRAWABLE_FOLDER);
``` 


#### Permissions ####
----
```
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
``` 



#### License ####
----
```
Copyright 2017 Adeyinka Adediji

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

#### Credits ####
---
* [Picasso](https://github.com/square/picasso)

