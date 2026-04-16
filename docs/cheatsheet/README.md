# 📋 Java Cheatsheet — Шуурхай харах

← [Home](../home/) | [Repo](../../)

Syntax мартсан бол эндээс шуурхай хар.

---

## 🔤 Хувьсагч (Variable) ба Төрөл (Type)

```java
int age = 20;             // бүхэл тоо
long big = 9_999_999_999L; // 32 бит-с дээш
double price = 19.99;     // бутархай
boolean alive = true;     // true / false
char grade = 'A';         // нэг тэмдэгт, single quote
String name = "Bob";      // үг, double quote

final int MAX = 100;      // тогтмол, өөрчлөгдөхгүй
var x = 10;               // Java 10+, автомат төрөл таах
```

---

## ⚙️ Оператор

```java
// Арифметик
+ - * / %

// Харьцуулах
== != < > <= >=

// Логик
&& (and)   || (or)   ! (not)

// Тоонд
++  --    // нэмэх/хасах нэгээр
+=  -=    // a = a + b → a += b
```

⚠️ `=` vs `==`:
- `=` — утга оноох
- `==` — тэнцүү эсэхийг шалгах
- **String**-д `.equals()` ашигла, `==` биш!

---

## 🔀 Нөхцөл ба давталт

```java
// If-else
if (age >= 18) {
    System.out.println("Насанд хүрсэн");
} else if (age >= 13) {
    System.out.println("Өсвөр");
} else {
    System.out.println("Хүүхэд");
}

// Switch (Java 14+)
String msg = switch (grade) {
    case 'A' -> "Маш сайн";
    case 'B' -> "Сайн";
    default  -> "Үл мэдэгдэх";
};

// For
for (int i = 0; i < 10; i++) { ... }

// For-each
for (String name : names) { ... }

// While
while (hp > 0) { ... }

// Do-while
do { ... } while (!done);

// Break / Continue
for (...) {
    if (found) break;      // loop-ээс бүрэн гарах
    if (skip) continue;    // дараагийн iteration руу үсрэх
}
```

---

## 📦 Array

```java
int[] nums = new int[5];           // 5 урттай
int[] primes = {2, 3, 5, 7, 11};   // литерал

nums[0] = 10;                      // оноох
int x = nums[0];                   // авах
int len = nums.length;             // урт (method биш, field)

// 2D array
int[][] grid = new int[3][3];
grid[1][2] = 5;

// Loop
for (int i = 0; i < nums.length; i++) { ... }
for (int n : nums) { ... }
```

---

## 🏛️ Class ба Object

```java
public class Character {

    // Field
    private String name;
    private int hp;

    // Constructor
    public Character(String name) {
        this.name = name;
        this.hp = 100;
    }

    // Getter / Setter
    public String getName() {
        return name;
    }

    public void setHp(int hp) {
        if (hp < 0) hp = 0;
        this.hp = hp;
    }

    // Method
    public void takeDamage(int amount) {
        hp = Math.max(0, hp - amount);
    }

    // toString override
    @Override
    public String toString() {
        return "Character{" + name + ", " + hp + "}";
    }
}

// Ашиглах
Character hero = new Character("Bob");
hero.takeDamage(30);
System.out.println(hero);
```

---

## 🧬 Inheritance

```java
class Animal {
    protected String name;
    public void eat() { ... }
}

class Dog extends Animal {
    public void bark() { ... }
}

// Constructor-д parent-ыг дуудах
class Warrior extends Character {
    public Warrior(String name) {
        super(name);         // Character(name) дуудна
    }
}

// Override
@Override
public void attack(Character target) {
    target.takeDamage(25);
}
```

---

## 🎭 Polymorphism

```java
Character[] party = {
    new Warrior("Bob"),
    new Mage("Alice"),
    new Rogue("Charlie")
};

for (Character c : party) {
    c.attack(enemy);   // тус бүр өөрийнхөөрөө attack хийнэ
}

// Instanceof
if (c instanceof Mage mage) {
    mage.castFireball(enemy);   // Java 16+ pattern matching
}
```

---

## 🎨 Abstraction

```java
// Abstract class
abstract class Skill {
    abstract void cast(Character c);

    public void logCast() {
        System.out.println("Casting skill");
    }
}

// Interface
interface Usable {
    void use();

    default void logUse() {         // default method (Java 8+)
        System.out.println("Used");
    }
}

class Potion implements Usable {
    @Override public void use() { ... }
}
```

---

## ⚠️ Exception

```java
// Try-catch
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("0-д хуваасан: " + e.getMessage());
} finally {
    // заавал ажиллах хэсэг
}

// Throw
if (amount < 0) {
    throw new IllegalArgumentException("Сөрөг байж болохгүй");
}

// Custom exception
class InsufficientGoldException extends Exception {
    public InsufficientGoldException(String msg) {
        super(msg);
    }
}

// Try-with-resources (файл гэх мэт)
try (BufferedReader r = new BufferedReader(new FileReader("file.txt"))) {
    String line = r.readLine();
}
```

---

## 📚 Collections

```java
import java.util.*;

// List
List<String> list = new ArrayList<>();
list.add("apple");
list.get(0);
list.remove(0);
list.size();

// Set (дубль үгүй)
Set<Integer> set = new HashSet<>();
set.add(5);
set.contains(5);

// Map (түлхүүр→утга)
Map<String, Integer> map = new HashMap<>();
map.put("bob", 100);
map.get("bob");
map.containsKey("bob");

// Loop
for (String s : list) { ... }

for (Map.Entry<String, Integer> e : map.entrySet()) {
    e.getKey();
    e.getValue();
}
```

---

## 📁 File I/O

```java
import java.io.*;

// Унших
try (BufferedReader r = new BufferedReader(new FileReader("save.txt"))) {
    String line;
    while ((line = r.readLine()) != null) {
        System.out.println(line);
    }
}

// Бичих
try (BufferedWriter w = new BufferedWriter(new FileWriter("save.txt"))) {
    w.write("Bob,50,100");
    w.newLine();
}
```

---

## 🔧 Хэрэгтэй Math / String

```java
// Math
Math.max(a, b);
Math.min(a, b);
Math.abs(-5);          // 5
Math.random();          // 0.0–1.0
Math.floor(3.7);        // 3.0
Math.ceil(3.2);         // 4.0
Math.pow(2, 10);        // 1024

// Random
Random r = new Random();
int n = r.nextInt(100);  // 0–99

// String
String s = "Hello";
s.length();
s.charAt(0);             // 'H'
s.substring(1, 4);       // "ell"
s.toLowerCase();
s.equals("hello");
s.equalsIgnoreCase("HELLO");
s.contains("ell");
s.split(",");
String.format("Hp: %d / %d", 50, 100);
```

---

## 📌 Access modifiers

| Modifier | Тухайн class | Ижил package | Subclass | Бүгд |
|---|---|---|---|---|
| `public`    | ✅ | ✅ | ✅ | ✅ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| *(default)* | ✅ | ✅ | ❌ | ❌ |
| `private`   | ✅ | ❌ | ❌ | ❌ |

**Зарчим:** боломжтой бол хамгийн хязгаарлагдмалыг (`private`) ашигла.

---

## 🔗 Илүү дэлгэрэнгүй

- [Oracle Java Tutorials](https://docs.oracle.com/javase/tutorial/)
- [Baeldung](https://www.baeldung.com/)
- [DevDocs Java](https://devdocs.io/openjdk~17/) — offline-д бас ажиллана
