# gradle 打印依赖树

./gradlew app:dependencies

通过依赖树具体排查, 找到问题根源，排除掉

./gradlew dependencies -q --configuration compile

