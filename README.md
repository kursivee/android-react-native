### Steps to import .aar dependencies from react native

- `cd jsfiles`
- `yarn install`
- `cd node_modules/react-native/android/com/facebook/react/react-native/0.60.3`
- `mvn install:install-file -Dfile=./react-native-0.60.3.aar -DgroupId=com.android -DartifactId=react-native -Dversion=0.60.3 -Dpackaging=aar`
- Add dependency in `build.gradle` `[groupId]:[artifactId]:[version]`
- In this case it would be `implementation "com.android:react-native:0.60.3"`
- Add `repositories { mavenLocal() }` to build.gradle
