# Kotlin의 Extension은 어떻게 동작하는가 part 1
https://medium.com/til-kotlin-ko/kotlin%EC%9D%98-extension%EC%9D%80-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%99%EC%9E%91%ED%95%98%EB%8A%94%EA%B0%80-part-1-7badafa7524a

# Kotlin의 Extension은 어떻게 동작하는가 part 2
https://medium.com/til-kotlin-ko/kotlin%EC%9D%98-extension%EC%9D%80-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%99%EC%9E%91%ED%95%98%EB%8A%94%EA%B0%80-part-2-fb52bb20bc9e

# Kotlin의 Extension은 어떻게 동작하는가 part 3
https://medium.com/til-kotlin-ko/kotlin%EC%9D%98-extension%EC%9D%80-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%99%EC%9E%91%ED%95%98%EB%8A%94%EA%B0%80-part-3-587cc37e7337

# Note
## Extension은 정적으로 처리된다.
```
fun String.extension() : String {
    return "$this extension."
}
```
위 코드를 디컴파일한 코드는 다음과 같다.
```
public final class ExtensionsKt {
   @NotNull
   public static final String extension(@NotNull String $receiver) {
      Intrinsics.checkParameterIsNotNull($receiver, "$receiver");
      return $receiver + " extension.";
   }
}
```
