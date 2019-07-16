### Steps to import .aar dependencies from react native

- `cd jsfiles`
- `yarn install`
- `cd node_modules/react-native/android/com/facebook/react/react-native/0.60.3`
- `mvn install:install-file -Dfile=./react-native-0.60.3.aar -DgroupId=com.android -DartifactId=react-native -Dversion=0.60.3 -Dpackaging=aar`
- Add dependency in `build.gradle` `[groupId]:[artifactId]:[version]`
- In this case it would be `implementation "com.android:react-native:0.60.3"`
- Add `repositories { mavenLocal() }` to build.gradle
- Or for a local artifactory add `repositories { maven { url 'http://localhost:8081/artifactory/libs-release' } }

### Setting up local artifactory

- Setup with docker https://www.jfrog.com/confluence/display/RTF/Installing+with+Docker
- Setting up authentication https://www.jfrog.com/confluence/display/RTF/Maven+Repository#MavenRepository-SettingUpSecurityinMavenSettings
- Deploy .aar by following here https://maven.apache.org/guides/mini/guide-3rd-party-jars-remote.html
- In this case run `mvn deploy:deploy-file -Dfile=./react-native-0.60.3.aar -DgroupId=com.android -DartifactId=react-native -Dversion=0.60.3 -Dpackaging=aar -DrepositoryId=central -Durl=http://localhost:8081/artifactory/libs-release`
