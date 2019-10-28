작성자 : gmlwo530

kotlin을 공부하다가 다음과 바깥 클래스의 변수를 참조하고 싶은데 참조가 되지 않았습니다.
구글링을 해보니 nested and inner class 개념이 있어 twl에 기록합니다.

```kotlin
  class Outer {
      private val bar: Int = 1
      class Inner {
          fun foo() = bar // bar를 참조 할 수 없습니다.
      }
  }
```

### Nested Class
기본적으로 class는 다른 class에 nested 될 수 있습니다

```kotlin
class Outer {
    private val bar: Int = 1
    class Nested {
        fun foo() = 2
    }
}

val demo = Outer.Nested().foo() // == 2
```

이때 nested 된 클래스에서 바깥 클래스의 변수를 참조 하고 싶으면 `inner`를 붙여주면 됩니다.

```kotlin
class Outer {
    private val bar: Int = 1
    inner class Nested {
        fun foo() = bar
    }
}

val demo = Outer().Nested().foo() // == 2
```
<br>

---
**Reference** : [https://kotlinlang.org/docs/reference/nested-classes.html](https://kotlinlang.org/docs/reference/nested-classes.html)
