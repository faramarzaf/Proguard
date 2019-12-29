# Proguard  


ProGuard is a tool to help **minify**, **obfuscate**, and **optimize** your code.  
It is not only especially useful for reducing the overall size of your Android application as well as removing unused classes and methods that contribute towards the intrinsic 64k method limit of Android applications.   
Because of the latter issue, ProGuard is often recommended to be used both in development and production especially for larger applications.

ProGuard can be enabled by using the `minifyEnabled` option for any build type. 
If you intend to use it for production, it is highly recommended you also enable it on your development. 
Without fully testing ProGuard on your development builds, you may encounter unexpected crashes or situations where the app does not function as expected.  
```gradle
android {
   buildTypes {
      dev {
          minifyEnabled true  // enables ProGuard
          proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
      }
}
```

An alternative is to request only to remove unwanted code (shrink) but not obfuscate.   
```gradle
buildTypes {
  debug {
    minifyEnabled true  // shrink
    useProguard false   // don't obfuscate
    proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
  }

  release {
    minifyEnabled true  // shrink
    useProguard true    // obfuscate
    proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
  }
}
```

