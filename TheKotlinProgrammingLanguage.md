# プログラミング言語Kotlin
## サンプルコード
ファイル名: hello.kt

```kotlin
fun main() {
    println("Hello, World!")
}
```

コンパイルと実行

```
$ kotlinc hello.kt -include-runtime -d hello.jar
$ java -jar hello.jar
Hello, World!
```

スクリプトとして実行（.kts）

```kotlin
#!/usr/bin/env kotlin
println("Hello, World!")
```

---

## 基本的な特徴

### コメント

```kotlin
// 単一行コメント
```

```kotlin
/* 複数行コメント */
```

```kotlin
/* ネストされた
   /* コメント */
   も使用可能 */
```

### セミコロン
省略可能（推奨）。複数の文を1行に書く場合のみ使用。

```kotlin
val x = 1; val y = 2
```

### パッケージとインポート

```kotlin
package com.example.myapp

import kotlin.text.*
import kotlin.math.sqrt
```

パッケージとディレクトリ構造の一致は必須ではない。

---

## 型

|名前|内容|
|:--|:--|
|Boolean|真偽値 (true, false)|
|Byte|符号あり8bit整数型|
|Short|符号あり16bit整数型|
|Int|符号あり32bit整数型|
|Long|符号あり64bit整数型|
|Float|単精度(32bit)浮動小数点|
|Double|倍精度(64bit)浮動小数点|
|Char|Unicode文字|
|String|文字列|
|UByte|符号なし8bit整数型|
|UShort|符号なし16bit整数型|
|UInt|符号なし32bit整数型|
|ULong|符号なし64bit整数型|
|Any|すべての型のスーパータイプ|
|Unit|Javaのvoidに相当|
|Nothing|値を返さないことを示す型|

### 数値リテラル

|接頭語・接尾語|説明|例|
|:--|:--|:--|
|-|10進数|256, 1024, 3.14|
|0b|2進数|0b10001011|
|0x|16進数|0xFF27|
|L|Long型|100L|
|f / F|Float型|3.14f|
|_|桁区切り|1_000_000|

```kotlin
val million = 1_000_000
val hex = 0xFF
val binary = 0b1010
val long = 100L
val float = 3.14f
```

### 型エイリアス

```kotlin
typealias UserMap = Map<String, User>
typealias ClickHandler = (Button) -> Unit
```

---

## 変数と定数

```kotlin
val name: String = "Kotlin"   // 不変（再代入不可）
var count: Int = 0             // 可変
```

### 型推論

```kotlin
val language = "Kotlin"   // String型と推論
var count = 0             // Int型と推論
```

### 遅延初期化

```kotlin
lateinit var name: String      // varのみ、null非許容型に使用
val result: String by lazy { computeValue() }  // 初回アクセス時に初期化
```

### トップレベル変数

```kotlin
val PI = 3.14159
var globalCounter = 0
```

---

## 演算子

### 算術演算子

|||
|:--|:--|
|+|加算|
|-|減算|
|*|乗算|
|/|除算|
|%|剰余|

### 代入演算子

|||
|:--|:--|
|=|代入|
|+=|加算代入|
|-=|減算代入|
|*=|乗算代入|
|/=|除算代入|
|%=|剰余代入|

### 比較演算子

||||
|:--|:--|:--|
|==|a == b|構造等価|
|!=|a != b|構造非等価|
|===|a === b|参照等価|
|!==|a !== b|参照非等価|
|<|a < b|小なり|
|<=|a <= b|小なりイコール|
|>|a > b|大なり|
|>=|a >= b|大なりイコール|

### 論理演算子

||||
|:--|:--|:--|
|!|!a|論理否定|
|&&|a && b|論理積|
|\|\||a \|\| b|論理和|

### ビット演算子

||||
|:--|:--|:--|
|and|a and b|ビット積|
|or|a or b|ビット和|
|xor|a xor b|ビット排他的論理和|
|inv|a.inv()|ビット反転|
|shl|a shl n|左シフト|
|shr|a shr n|右シフト（符号あり）|
|ushr|a ushr n|右シフト（符号なし）|

### 範囲演算子

||||
|:--|:--|:--|
|..|1..5|閉区間（1〜5）|
|..<|1..<5|半開区間（1〜4）|
|downTo|5 downTo 1|降順|
|step|1..10 step 2|ステップ指定|

---

## 文字と文字列

```kotlin
val ch: Char = 'A'
val str: String = "Hello, World!"
```

### 文字列テンプレート

```kotlin
val name = "Kotlin"
val greeting = "Hello, $name!"
val length = "Length: ${name.length}"
val calc = "1 + 2 = ${1 + 2}"
```

### 複数行文字列

```kotlin
val text = """
    First line
    Second line
    Third line
""".trimIndent()
```

### 文字列操作

```kotlin
val s = "Hello"
s.length           // 5
s.uppercase()      // "HELLO"
s.lowercase()      // "hello"
s.reversed()       // "olleH"
s.contains("ell")  // true
s.startsWith("He") // true
s.replace("l", "r") // "Herro"
"$s World".split(" ")  // ["Hello", "World"]
```

---

## 配列

```kotlin
val arr = arrayOf(1, 2, 3, 4, 5)
val zeros = IntArray(5)              // [0, 0, 0, 0, 0]
val filled = IntArray(3) { it * 2 } // [0, 2, 4]
```

```kotlin
arr[0]              // 先頭要素
arr[arr.size - 1]   // 末尾要素
arr.size            // 要素数
for (n in arr) { println(n) }
```

---

## コレクション

### List

```kotlin
val list = listOf(1, 2, 3, 4, 5)         // 読み取り専用
val mList = mutableListOf(1, 2, 3)        // 可変

mList.add(4)
mList.removeAt(0)
mList[0] = 10

list.size
list[2]
list.indexOf(3)
list.contains(2)      // true
list.first()
list.last()
```

### Set

```kotlin
val set = setOf(1, 2, 3, 2, 1)    // {1, 2, 3} 重複排除
val mSet = mutableSetOf(1, 2, 3)

mSet.add(4)
mSet.remove(1)

set.contains(2)    // true
set.size           // 3
```

### Map

```kotlin
val map = mapOf("a" to 1, "b" to 2, "c" to 3)  // 読み取り専用
val mMap = mutableMapOf("a" to 1, "b" to 2)      // 可変

mMap["c"] = 3
mMap.put("d", 4)
mMap.remove("a")

map["a"]                  // 1
map.getOrDefault("z", 0)  // 0
map.keys                  // [a, b, c]
map.values                // [1, 2, 3]
map.containsKey("b")      // true
```

### コレクション操作

```kotlin
val numbers = listOf(1, 2, 3, 4, 5, 6)

numbers.filter { it % 2 == 0 }          // [2, 4, 6]
numbers.map { it * 2 }                  // [2, 4, 6, 8, 10, 12]
numbers.reduce { acc, n -> acc + n }    // 21
numbers.fold(0) { acc, n -> acc + n }   // 21
numbers.any { it > 4 }                  // true
numbers.all { it > 0 }                  // true
numbers.none { it > 10 }               // true
numbers.count { it % 2 == 0 }          // 3
numbers.sortedBy { it }
numbers.sortedByDescending { it }
numbers.groupBy { it % 2 == 0 }
numbers.take(3)                         // [1, 2, 3]
numbers.drop(3)                         // [4, 5, 6]
numbers.sum()
numbers.max()
numbers.min()
numbers.average()
```

### ArrayDeque

```kotlin
val deque = ArrayDeque(listOf(1, 2, 3))
deque.addFirst(0)
deque.addLast(4)
deque.removeFirst()
deque.removeLast()
```

---

## 関数

```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}
```

### 単一式関数

```kotlin
fun add(a: Int, b: Int): Int = a + b
fun greet(name: String) = "Hello, $name!"
```

### デフォルト引数・名前付き引数

```kotlin
fun greet(name: String, greeting: String = "Hello") = "$greeting, $name!"

greet("Alice")                    // Hello, Alice!
greet("Bob", greeting = "Hi")    // Hi, Bob!
greet(greeting = "Hey", name = "Carol")
```

### 可変長引数

```kotlin
fun sum(vararg numbers: Int): Int = numbers.sum()

sum(1, 2, 3, 4)   // 10
val arr = intArrayOf(1, 2, 3)
sum(*arr)          // スプレッド演算子でArrayを展開
```

### Unit（戻り値なし）

```kotlin
fun printMessage(msg: String): Unit {
    println(msg)
}
// Unit は省略可能
fun printMessage(msg: String) {
    println(msg)
}
```

### 再帰・末尾再帰

```kotlin
tailrec fun factorial(n: Int, acc: Int = 1): Int =
    if (n <= 1) acc else factorial(n - 1, n * acc)
```

### ローカル関数

```kotlin
fun outer() {
    fun inner(x: Int) = x * 2
    println(inner(5))
}
```

---

## ラムダと高階関数

### ラムダ式

```kotlin
val double: (Int) -> Int = { x -> x * 2 }
val add: (Int, Int) -> Int = { a, b -> a + b }
val greet: () -> String = { "Hello!" }
```

### `it` — 単一パラメータの省略

```kotlin
val double = { x: Int -> x * 2 }
listOf(1, 2, 3).map { it * 2 }   // itは暗黙的なパラメータ名
```

### 高階関数

```kotlin
fun operate(a: Int, b: Int, op: (Int, Int) -> Int): Int = op(a, b)

operate(3, 5) { x, y -> x + y }   // 8
```

### 末尾ラムダ（Trailing Lambda）

```kotlin
// 最後の引数が関数の場合、括弧の外に記述可能
listOf(1, 2, 3).forEach { println(it) }
run { println("実行") }
```

### 関数参照

```kotlin
fun double(x: Int) = x * 2

val fn = ::double
listOf(1, 2, 3).map(::double)
listOf("a", "b").map(String::uppercase)
```

### クロージャ（外部変数のキャプチャ）

```kotlin
var sum = 0
listOf(1, 2, 3).forEach { sum += it }
println(sum)   // 6
```

---

## クラス

```kotlin
class Person(val name: String, var age: Int) {
    val description: String
        get() = "Name: $name, Age: $age"

    fun greet(): String = "Hi, I'm $name"
}

val person = Person("Alice", 30)
println(person.name)
println(person.greet())
```

### init ブロック・セカンダリコンストラクタ

```kotlin
class Person(val name: String, var age: Int) {
    init {
        require(age > 0) { "age must be positive" }
    }

    constructor(name: String) : this(name, 0)
}
```

### プロパティ

```kotlin
class Circle(val radius: Double) {
    val area: Double
        get() = Math.PI * radius * radius

    var diameter: Double
        get() = radius * 2
        set(value) { /* radius = value / 2 */ }
}
```

### アクセス修飾子

|修飾子|説明|
|:--|:--|
|public|どこからでもアクセス可能（デフォルト）|
|internal|同一モジュール内からアクセス可能|
|protected|同一クラスとサブクラスからアクセス可能|
|private|同一クラス内からのみアクセス可能|

```kotlin
class MyClass {
    public val publicProp = 1
    internal val internalProp = 2
    protected val protectedProp = 3
    private val privateProp = 4
}
```

---

## 継承

クラスはデフォルトで `final`。継承を許可するには `open` が必要。

```kotlin
open class Animal(val name: String) {
    open fun sound(): String = "..."
    fun describe() = "$name says ${sound()}"
}

class Dog(name: String) : Animal(name) {
    override fun sound(): String = "Woof"
}

val dog = Dog("Rex")
dog.describe()   // Rex says Woof
```

### final / abstract

```kotlin
open class Base {
    open fun method() {}
    final fun locked() {}   // オーバーライド禁止
}

abstract class Shape {
    abstract fun area(): Double   // 実装必須
    fun describe() = "Area: ${area()}"
}
```

---

## データクラス

```kotlin
data class User(val name: String, val age: Int)
```

自動生成される機能：`equals()`/`hashCode()`、`toString()`、`copy()`、`componentN()`

```kotlin
val user1 = User("Alice", 30)
val user2 = user1.copy(age = 31)
println(user1)            // User(name=Alice, age=30)
println(user1 == user2)   // false

// デストラクチャリング
val (name, age) = user1
println("$name is $age")
```

---

## オブジェクト

### オブジェクト宣言（シングルトン）

```kotlin
object AppConfig {
    val appName = "MyApp"
    val version = "1.0"
    fun describe() = "$appName v$version"
}

AppConfig.describe()
```

### コンパニオンオブジェクト

```kotlin
class MyClass {
    companion object {
        val TAG = "MyClass"
        fun create() = MyClass()
    }
}

MyClass.TAG
MyClass.create()
```

### 匿名オブジェクト

```kotlin
val listener = object : ClickListener {
    override fun onClick() { println("clicked") }
}
```

---

## インターフェース

```kotlin
interface Drawable {
    val color: String        // 抽象プロパティ
    fun draw()               // 抽象メソッド
    fun describe() = "Drawing in $color"  // デフォルト実装
}

class Circle(override val color: String) : Drawable {
    override fun draw() { println("Drawing circle") }
}
```

複数インターフェースの実装：

```kotlin
class MyClass : InterfaceA, InterfaceB {
    override fun methodA() {}
    override fun methodB() {}
}
```

---

## 列挙型

```kotlin
enum class Direction { NORTH, SOUTH, WEST, EAST }
```

### プロパティ付き enum

```kotlin
enum class Color(val rgb: Int) {
    RED(0xFF0000),
    GREEN(0x00FF00),
    BLUE(0x0000FF)
}

val c = Color.RED
println(c.name)    // RED
println(c.ordinal) // 0
println(c.rgb)     // 16711680
```

### enum のメソッド

```kotlin
enum class Planet(val mass: Double) {
    EARTH(5.972e24),
    MARS(6.417e23);

    fun surfaceGravity() = mass / 1e24
}

// すべての値を取得
for (dir in Direction.entries) println(dir)
Direction.valueOf("NORTH")
```

---

## シールドクラス

```kotlin
sealed class Result<out T> {
    data class Success<T>(val data: T) : Result<T>()
    data class Failure(val error: Throwable) : Result<Nothing>()
    object Loading : Result<Nothing>()
}

fun handle(result: Result<String>) = when (result) {
    is Result.Success -> println("Data: ${result.data}")
    is Result.Failure -> println("Error: ${result.error.message}")
    Result.Loading    -> println("Loading...")
}
```

---

## Null安全

### Nullable型

```kotlin
var a: String = "hello"   // null不可
var b: String? = null     // null許容
```

### セーフコール演算子 `?.`

```kotlin
val length = b?.length            // bがnullならnullを返す
val head = list?.first()?.name    // チェーン可能
```

### エルビス演算子 `?:`

```kotlin
val len = b?.length ?: 0          // nullなら0
val name = input ?: throw IllegalArgumentException("name required")
```

### Not-null アサーション `!!`

```kotlin
val len = b!!.length   // nullならNullPointerException
```

### スマートキャスト

```kotlin
if (b != null) {
    println(b.length)   // null非許容として扱われる
}
```

### セーフキャスト `as?`

```kotlin
val str: String? = obj as? String   // キャスト失敗時はnull
```

### let との組み合わせ

```kotlin
b?.let { println("Value: $it") }
```

---

## 制御フロー

### if 式

```kotlin
val max = if (a > b) a else b

val grade = if (score >= 90) "A"
    else if (score >= 80) "B"
    else "C"
```

### when 式

```kotlin
val result = when (x) {
    0 -> "zero"
    1, 2 -> "one or two"
    in 3..10 -> "3 to 10"
    is String -> "a string"
    else -> "other"
}

// 引数なし when
when {
    x < 0 -> println("negative")
    x == 0 -> println("zero")
    else -> println("positive")
}
```

### for ループ

```kotlin
for (i in 1..5) print(i)          // 12345
for (i in 1..<5) print(i)         // 1234
for (i in 5 downTo 1) print(i)    // 54321
for (i in 1..10 step 2) print(i)  // 13579

val list = listOf("a", "b", "c")
for (item in list) println(item)
for ((index, item) in list.withIndex()) println("$index: $item")
```

### while ループ

```kotlin
while (condition) { ... }

do {
    ...
} while (condition)
```

### break / continue / return ラベル

```kotlin
outer@ for (i in 1..5) {
    for (j in 1..5) {
        if (j == 3) break@outer
        if (j == 2) continue@outer
    }
}
```

---

## 拡張関数・拡張プロパティ

### 拡張関数

```kotlin
fun String.isPalindrome(): Boolean = this == this.reversed()

fun Int.isEven(): Boolean = this % 2 == 0

"racecar".isPalindrome()   // true
4.isEven()                 // true
```

### ジェネリック拡張関数

```kotlin
fun <T> List<T>.secondOrNull(): T? = if (size >= 2) this[1] else null
```

### 拡張プロパティ

```kotlin
val String.wordCount: Int
    get() = split(" ").size

val Int.doubled: Int
    get() = this * 2

"hello world".wordCount   // 2
5.doubled                 // 10
```

---

## スコープ関数

|関数|オブジェクト参照|戻り値|用途|
|:--|:--|:--|:--|
|let|it|ラムダ結果|null安全処理・変換|
|run|this|ラムダ結果|設定＋結果取得|
|with|this|ラムダ結果|メソッド呼び出しのグループ化|
|apply|this|レシーバー自身|オブジェクトの設定|
|also|it|レシーバー自身|副作用（ログなど）|

```kotlin
// let — null安全チェックや変換
val length = str?.let { it.trim().length } ?: 0

// apply — オブジェクト設定
val person = Person("Alice").apply {
    age = 30
    city = "Tokyo"
}

// run — 設定と結果計算
val result = service.run {
    url = "https://example.com"
    connect()
}

// with — メソッド呼び出しのグループ化
with(numbers) {
    println("size: $size")
    println("first: ${first()}")
}

// also — 副作用（チェーンを崩さない）
numbers.also { println("Before: $it") }.add(4)
```

---

## 型チェックとキャスト

### is / !is 演算子

```kotlin
if (obj is String) println("String length: ${obj.length}")
if (obj !is Int) println("Not an Int")
```

### スマートキャスト

```kotlin
fun describe(obj: Any): String = when (obj) {
    is String -> "String of length ${obj.length}"
    is Int    -> "Int: $obj"
    is List<*> -> "List with ${obj.size} elements"
    else      -> "Unknown"
}
```

### 明示的キャスト

```kotlin
val str = obj as String         // 失敗時に ClassCastException
val str = obj as? String        // 失敗時に null
```

---

## ジェネリクス

```kotlin
fun <T> identity(value: T): T = value

class Box<T>(val content: T) {
    fun get(): T = content
}

val box = Box(42)
val content = box.get()   // Int
```

### 型制約

```kotlin
fun <T : Comparable<T>> max(a: T, b: T): T = if (a > b) a else b

fun <T> sort(list: MutableList<T>) where T : Comparable<T>, T : Cloneable { }
```

### 分散（variance）

```kotlin
class Producer<out T>(val value: T)  // 共変（covariant）
class Consumer<in T> { fun consume(value: T) {} }  // 反変（contravariant）
```

### 具体化型パラメータ（reified）

```kotlin
inline fun <reified T> isInstance(value: Any): Boolean = value is T

isInstance<String>("hello")   // true
isInstance<Int>("hello")      // false
```

---

## エラー処理

```kotlin
try {
    val result = riskyOperation()
} catch (e: IllegalArgumentException) {
    println("Argument error: ${e.message}")
} catch (e: Exception) {
    println("Error: ${e.message}")
} finally {
    println("Always executed")
}
```

### 例外のスロー

```kotlin
fun validate(age: Int) {
    if (age < 0) throw IllegalArgumentException("age must be non-negative")
}
```

### try 式

```kotlin
val value = try { riskyOp() } catch (e: Exception) { -1 }
```

### runCatching

```kotlin
val result = runCatching { riskyOperation() }
result.onSuccess { println("Success: $it") }
result.onFailure { println("Error: ${it.message}") }
val value = result.getOrDefault(-1)
```

---

## 並行処理（コルーチン）

### 基本的なコルーチン起動

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!")
    }
    println("Hello")
}
// Hello
// World!
```

### async / await

```kotlin
val deferred = async { fetchData() }
val result = deferred.await()
```

### suspend 関数

```kotlin
suspend fun fetchUser(id: Int): User {
    delay(1000L)   // 非ブロッキングな待機
    return User(id, "Alice")
}
```

### Flow（非同期ストリーム）

```kotlin
import kotlinx.coroutines.flow.*

fun numbers(): Flow<Int> = flow {
    for (i in 1..3) {
        delay(100)
        emit(i)
    }
}

// 収集
numbers().collect { println(it) }
```

### コルーチンコンテキスト・ディスパッチャー

|ディスパッチャー|説明|
|:--|:--|
|Dispatchers.Default|CPU集中タスク|
|Dispatchers.IO|I/Oタスク（ファイル、ネットワーク）|
|Dispatchers.Main|UIスレッド（Androidなど）|
|Dispatchers.Unconfined|制約なし|

```kotlin
withContext(Dispatchers.IO) {
    // I/O処理
}
```

---

## Java相互運用性

```kotlin
// JavaクラスをKotlinから使用
import java.util.ArrayList

val list = ArrayList<String>()
list.add("Kotlin")

// Javaのstaticメソッドへのアクセス
val thread = Thread.currentThread()
println(thread.name)
```

### @JvmStatic / @JvmField

```kotlin
class MyClass {
    companion object {
        @JvmStatic fun create() = MyClass()
        @JvmField val TAG = "MyClass"
    }
}
// Javaから: MyClass.create(), MyClass.TAG
```

### @JvmOverloads

```kotlin
@JvmOverloads
fun greet(name: String, greeting: String = "Hello"): String = "$greeting, $name!"
// Javaからオーバーロードとして見える
```

---

## 参考資料

- [Kotlin公式ドキュメント（英語）](https://kotlinlang.org/docs/home.html)
- [Android向けKotlin入門（日本語）](https://developer.android.com/kotlin/learn?hl=ja)
- [Kotlin言語仕様](https://kotlinlang.org/spec/)
- [Kotlin標準ライブラリ API](https://kotlinlang.org/api/latest/jvm/stdlib/)
