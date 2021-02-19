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
확장 대상(Receiver)인 `String`을 인자로 받는 `static final`로 메소드가 생성된다. 이는 클래스 자체가 확장된 것이 아니라, 정적인 메소드 형태로 코드가 생성되었으므로, 객체 멤버 접근에 제한이 존재할 수 있다는 뜻으로 해석할 수 있다. 이 특성은 [Extension are resolved statically]( https://kotlinlang.org/docs/extensions.html#extensions-are-resolved-statically "Extension are resolved statically")
