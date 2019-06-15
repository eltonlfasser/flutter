1st Thing I want to do is document the google dependency issues.
There quite a bit of issues around with incompatible packages, having to use older packages etc....

I'm not sure if this will work for every scenario, alot of other "workarounds" I've come across just didnt work.

My setup at the moment goes like this.

# android\gradle.properties

If you intend using android x

android.useAndroidX=true
android.enableJetifier=true


# build.gradle
Replaced with what was there with

android\build.gradle
    dependencies {
        classpath 'com.android.tools.build:gradle:3.3.0'
        classpath 'com.google.gms:google-services:4.0.1'
    }
}

# android\app\build.gradle

Add multiDexEnabled true to defaultConfig

    defaultConfig {
        // TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).
        applicationId "applicationId"
        minSdkVersion 16
        targetSdkVersion 28
        multiDexEnabled true
        versionCode flutterVersionCode.toInteger()
        versionName flutterVersionName
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }

Add The following dependencies

dependencies {
    testImplementation 'junit:junit:4.12'
    implementation 'com.google.firebase:firebase-core:16.0.4'
    implementation 'com.google.firebase:firebase-auth:16.0.4'
    implementation 'androidx.core:core:1.0.1'
}

apply plugin: 'com.google.gms.google-services'

and lastly diasble version check.

com.google.gms.googleservices.GoogleServicesPlugin.config.disableVersionCheck = true
