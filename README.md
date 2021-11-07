## Android Architecture Components : ViewModel and ViewModelFactory - Starter Code


## 1. Introduction

- You use the `ViewModel` class to store and manage UI-related data in a lifecycle-conscious way. The `ViewModel` class allows data to survive device-configuration changes such as screen rotations and changes to keyboard availability.
- You use the `ViewModelFactory` class to instantiate and return the `ViewModel` object that survives configuration changes.
- This starter app is a two player game, GuessTheWord. It is a word guessing app you can play with one or more friends. To play, hold the device in landscape, facing away from you with your thumbs on the **Skip** and **Got It** buttons. Your friends can then give you clues to help you guess the word. If you get the word right, press **Got It**. If you're stuck, press **Skip**. You will modify the app to use Architecture components and best practices.



## 2. What you'll learn

- How to use the recommended Android app architecture
- How to use the `Lifecycle`, `ViewModel`, and `ViewModelFactory` classes in your app.
- How to retain UI data through device-configuration changes.
- What the factory method design pattern is and how to use it.
- How to create a **ViewModel** object using the interface **ViewModelProvider.Factory**.



## 3. Code walkthrough

https://developer.android.com/codelabs/kotlin-android-training-view-model?index=..%2F..android-kotlin-fundamentals#2



### 4. Find problems in the starter app()

- The starter app doesn't save and restore the app state during configuration changes, such as when the device orientation changes, or when the app shuts down and restarts. 
- The game screen does not navigate to the score screen when the user taps the **End Game** button.



### 5. App architecture

In this set of four codelabs, the improvements that you make to the GuessTheWord app follow the [Android app architecture](https://developer.android.com/jetpack/docs/guide) guidelines, and you use [Android Architecture Components](https://developer.android.com/jetpack/#architecture-components). The Android app architecture is similar to the [MVVM](https://en.wikipedia.org/wiki/Model–view–viewmodel) (model-view-viewmodel) architectural pattern.

##### 1. UI controller : `Activity` or `Fragment`

##### 2. ViewModel : Parts that holding data to be displayed in a fragment or activity.

- ViewModel starts with Activity's `onCreate()` method.
- ViewModel ends with `onCleared()` method itself.

##### 3. ViewModelFactory (instantiates ViewModel objects)



#### Reason to Separate the roles

###### 1. UI based class should deal with the interaction btw US and OS.

###### 2. To manage data not relying on the life-cycle.

###### 3. Alternative to use `onSaveInstanceState()` is not proper.

> You could resolve this issue using the [`onSaveInstanceState()`](https://developer.android.com/guide/components/activities/activity-lifecycle#save-simple-lightweight-ui-state-using-onsaveinstancestate) callback. However, using the `onSaveInstanceState()` method requires you to write extra code to save the state in a bundle, and to implement the logic to retrieve that state. Also, the amount of data that can be stored is minimal.











### License

Copyright 2019 Google, Inc.

Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements. See the NOTICE file distributed with this work for additional information regarding copyright ownership. The ASF licenses this file to you under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License..



