# android-image-picker
Android library project for choose multiple images from the device.

## [中文](https://github.com/sd6352051/android-image-picker/blob/master/README-ZH.md)
# Screenshot
![Image][1]

# Gradle
``` groovy
repositories { 
    maven { url "https://jitpack.io" }
}
dependencies {
    compile 'com.github.sd6352051:android-image-picker:v1.0.2'
}
```

#How to get started
### Step 0:  Permission 
``` xml
	<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```


### Step 1:  extends `BaseGalleryActivity` 
``` java
public class YourActivity extends BaseGalleryActivity{

}
```
### Step 2:  add android-image-picker root view on your layout
``` xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">
    <FrameLayout
        android:id="@+id/gallery_root"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        />
</RelativeLayout>      
```
### Step 3:  call `attachFragment(R.id.gallery_root)` method on YourActivity
``` java 
  @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        attachFragment(R.id.gallery_root);
    }
```

### Step 4: Implements interface
``` java
  @Override
    public Configuration getConfiguration() {
        //return your configuration
        Configuration cfg=new Configuration.Builder()
                .hasCamera(true)
                .hasShade(true)
                .hasPreview(true)
                .setSpaceSize(3)
                .setPhotoMaxWidth(120)
                .setCheckBoxColor(0xFF3F51B5)
                .setDialogHeight(Configuration.DIALOG_HALF)
                .setDialogMode(Configuration.DIALOG_GRID)
                .setMaximum(9)
                .setTip(null)
                .setAblumsTitle(null)
                .build();
        return cfg;
    }

    @Override
    public List<PhotoEntry> getSelectPhotos() {
        //return your selected photos
        return mSelectedPhotos;
    }

    @Override
    public void onSelectedCountChanged(int count) {
        //This method will be invoked when the selected photo count is changed.
        //count: selected photos count
    }

    @Override
    public void onAlbumChanged(String name) {
        //This method will be invoked when the albums name is changed.
        //name: current albums name
    }

    @Override
    public void onTakePhoto(PhotoEntry entry) {
        //This method will be invoked when you take the photo.
        //entry: take photo information just now
    }

    @Override
    public void onChoosePhotos(List<PhotoEntry> entries) {
        //This method will be invoked when you choose photos then call sendPhotos() method.
        //entries: selected photos information
    }

    @Override
    public void onPhotoClick(PhotoEntry entry) {
        //This method will be invoked when you click photo
        //entry： clicked photo information
    }

```
### Step 5:  some method

`openAlbum()`: opne albums 

`sendPhotos()`: `onChoosePhotos(List<PhotoEntry> entries)` method will be called 

[see the source cede of sample](https://github.com/sd6352051/android-image-picker/tree/master/app)

[download sample apk](https://github.com/sd6352051/android-image-picker/blob/master/sample.apk)

# Configuration
default configuration
``` java
Configuration cfg=new Configuration.Builder()
                //Flag to indicate that this view has a camera button
                .hasCamera(true)
                //Flag to indicate that this photo view has a layer mask
                .hasShade(true)
                //Flag to indicate that this photo view clickable
                .hasPreview(true)
                //GridView spacing between rows and columns
                .setSpaceSize(4)
                //Maximum width of photos
                .setPhotoMaxWidth(120)
                //Checkbox background color
                .setCheckBoxColor(0xFF3F51B5)
                //ablums dialog height
                .setDialogHeight(Configuration.DIALOG_HALF)
                //ablums dialog mode
                .setDialogMode(Configuration.DIALOG_GRID)
                //maximum photos selection limit
                .setMaximum(9)
                //Toast of maximum photos selection limit
                .setTip(null)
                //ablums dialog title
                .setAblumsTitle(null)
                .build();
```
  

# License
Copyright 2016 litao.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.













[1]: https://github.com/sd6352051/android-image-picker/blob/master/gif/gallery.gif
