# LivingTabs
Youtube Gaming inspired Tabs

![demo](art/demo.gif)

LivingTabs is based on TabLayout,so you get the same simple API with a beautiful and intuitive interface.

##How to use it?
Setup LivingTabs in the same way you setup TabLayout with ViewPager and then make the pager's adapter implements either [`DrawableIconAdapter`](/livingtabs/src/main/java/com/saiff35/livingtabs/LivingTabsLayout.java#L305) or [`DrawableResIconAdapter`](/livingtabs/src/main/java/com/saiff35/livingtabs/LivingTabsLayout.java#L311)

Here is an example:

####1)Declare your layout

####activity_main.xml
```xml

<android.support.design.widget.CoordinatorLayout
    android:layout_height="match_parent"
    android:layout_width="match_parent"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <android.support.design.widget.AppBarLayout
        android:id="@+id/appbar"
        android:layout_height="wrap_content"
        android:layout_width="match_parent"
        android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar">

        <!--Toolbar here-->
       
        <com.saiff35.livingtabs.LivingTabsLayout
            android:id="@+id/tabs"
            android:layout_height="wrap_content"
            android:layout_width="match_parent"
            android:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
            app:tabIndicatorColor="?attr/android:textColorPrimary" />

    </android.support.design.widget.AppBarLayout>

    <!--View Pager Here-->


</android.support.design.widget.CoordinatorLayout>

```

####2)Setup Tabs with a ViewPager
####MainActivity  
```java
  @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        //Setup Toolbar here
        
        MainAdapter mainAdapter = //Instanciate Adapter here
        
        viewPager.setAdapter(mainAdapter);
        tabs.setupWithViewPager(viewPager);

    }
```

####3)Make the pager's adapter implements either [`DrawableIconAdapter`](/livingtabs/src/main/java/com/saiff35/livingtabs/LivingTabsLayout.java#L305) or [`DrawableResIconAdapter`](/livingtabs/src/main/java/com/saiff35/livingtabs/LivingTabsLayout.java#L311)
####MainAdapter
```java
 public class MainAdapter extends FragmentPagerAdapter implements LivingTabsLayout.DrawableResIconAdapter {
      
      //Your FragmentPagerAdapter implementation here

        @Override
        public int getIcon(int position) {
            switch (position) {
                case 1:
                    return R.drawable.ic_home;
                case 0:
                    return R.drawable.ic_fire;
                case 2:
                    return R.drawable.ic_account;
            }
            return -1;
        }
    }
```
*PS:For curious people wondering what happens if the adapter implements both IconAdapters,LivingTabs will use [`DrawableResIconAdapter`](/livingtabs/src/main/java/com/saiff35/livingtabs/LivingTabsLayout.java#L311).*

##How to set it up with Gradle?

####1) Add dependency in your module build.gradle file
In *dependencies* add:

    compile ('com.github.saiff35:livingtabs:0.1.0') {
        exclude module: 'design'
    }
        
Make sure to add the latest version of the lib

####2) Use it to keep building your amazing apps :+1:

##Author
  Saif Chaouachi
  
<a href="https://plus.google.com/+SaifChaouachi/posts">
  <img  alt="Follow me on Google+"
    src="https://github.com/saiff35/LivingTabs/blob/master/art/gplus_64.png"/>
</a>
<a href="https://tn.linkedin.com/in/saifchaouachi">
  <img alt="Follow me on LinkedIn"
       src="https://github.com/saiff35/LivingTabs/blob/master/art/linkedin_64.png" />
</a>
<a href="https://twitter.com/SaifSaiff35">
  <img alt="Follow me on Twitter"
       src="https://github.com/saiff35/LivingTabs/blob/master/art/twitter_64.png" />
</a>




##License

LivingTabs is released under the **Apache License 2.0**

    Copyright (c) 2015 Saif Chaouachi
    
        Licensed under the Apache License, Version 2.0 (the "License");
        you may not use this file except in compliance with the License.
        You may obtain a copy of the License at
    
           http://www.apache.org/licenses/LICENSE-2.0
    
        Unless required by applicable law or agreed to in writing, software
        distributed under the License is distributed on an "AS IS" BASIS,
        WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
        See the License for the specific language governing permissions and
        limitations under the License.
