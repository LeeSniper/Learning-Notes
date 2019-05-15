# gradle 打印依赖树

./gradlew app:dependencies

通过依赖树具体排查, 找到问题根源，排除掉

./gradlew dependencies -q --configuration compile

*clean project
./gradlew clean

*build project
./gradlew build

*build for debug package
./gradlew assembleDebug or ./gradlew aD

*build for release package
./gradlew assembleRelease or ./gradlew aR

*build for release package and install
./gradlew installRelease or ./gradlew iR Release

*build for debug package and install
./gradlew installDebug or ./gradlew iD Debug

*uninstall release package
./gradlew uninstallRelease or ./gradlew uR

*uninstall debug package
./gradlew uninstallDebug or ./gradlew uD 

*all the above command + "--info" or "--debug" or "--scan" or "--stacktrace" can get more detail information.
