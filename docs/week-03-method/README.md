# Week 3 — Method & Code Reuse

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab3-methods](../../../../lab3-methods)

**Нэг өгүүлбэрээр:** Method гэдэг нь нэг удаа бичсэн логикаа "нэрлэж" хадгалсан блок — үүнээс хойш олон удаа дуудаж, програмаа богино, цэвэрхэн болгож чадна.

---

## 🎯 Энэ долоо хоногт сурах

1. Method зарлах: return type, нэр, parameter, body
2. `return` keyword — утга буцаах vs `void`
3. Нэг method-г өөр method-оос дуудах (decomposition)
4. Method overloading — ижил нэртэй, өөр parameter-тэй method

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java methods](https://www.youtube.com/watch?v=tVq9QIYnfVQ) | 11 мин | 🟢 Эхлэгч |
| [Coding with John — Java Methods Explained](https://www.youtube.com/@CodingWithJohn/search?query=methods) | 14 мин | 🟢 Эхлэгч |
| [Telusko — Methods in Java](https://www.youtube.com/@Telusko/search?query=methods+java) | 9 мин | 🟢 Эхлэгч |
| [Neso Academy — Method Overloading](https://www.youtube.com/@nesoacademy/search?query=method+overloading) | 10 мин | 🟡 Дунд |

**Хамгийн бага:** Bro Code-ийн видеог үзэж, дараа нь overloading-ийг тусад нь үз.

---

## 📖 Унших

- [Oracle — Defining Methods](https://docs.oracle.com/javase/tutorial/java/javaOO/methods.html) — албан ёсны
- [W3Schools — Java Methods](https://www.w3schools.com/java/java_methods.asp) — цэвэрхэн
- [Baeldung — Method Overloading and Overriding](https://www.baeldung.com/java-method-overload-override) — төстэй ойлголтуудыг ялгах
- [GeeksForGeeks — Methods in Java](https://www.geeksforgeeks.org/methods-in-java/) — олон жишээ

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Method](https://www.hackerrank.com/challenges/java-method/problem) — функц бичих
- [Exercism — Reverse String (Java)](https://exercism.org/tracks/java/exercises/reverse-string) — нэг method-той даалт
- [HyperSkill — Method basics](https://hyperskill.org/learn/topic/1998) — интерактив

---

## 💡 Code жишээ

**❌ Муу (давталт их, бүх логик `main` дотор):**
```java
public class Main {
    public static void main(String[] args) {
        int a = 5, b = 3;
        System.out.println("Sum: " + (a + b));
        System.out.println("Diff: " + (a - b));

        int c = 10, d = 2;
        System.out.println("Sum: " + (c + d));
        System.out.println("Diff: " + (c - d));
    }
}
```

**✅ Сайн (method-оор задалсан):**
```java
public class Calculator {
    public static int add(int x, int y) {
        return x + y;
    }

    public static int subtract(int x, int y) {
        return x - y;
    }

    public static void printResults(int a, int b) {
        System.out.println("Sum: " + add(a, b));
        System.out.println("Diff: " + subtract(a, b));
    }

    public static void main(String[] args) {
        printResults(5, 3);
        printResults(10, 2);
    }
}
```

Ялгаа:
- `add`, `subtract` нь нэг ажил **нэг method** — дахин хэрэглэж болно
- `main` бол зөвхөн "зохион байгуулагч" — дэлгэрэнгүй логикгүй
- `int` return хийдэг method нь `void`-с ялгаатай — утгыг дахин ашиглана

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `void` ба `int` return type-тай method-ын ялгаа?
2. Method-д parameter дамжуулах үед pass by value vs pass by reference юу хамаатай вэ?
3. `static` method ба instance method-ын ялгаа? (Week 5 preview)
4. Method overloading болох 2 шалгуур? Return type өөр байхад overloading болох уу?
5. Нэг method-н дотоод урт хэдэн мөр хүртэл байх сайн вэ?

---

## 🏆 Challenge

- HackerRank — "Java Varargs — Simple Addition" — `int... nums` хэрэглэх
- `isPrime(int n)` method бичиж, 1-100 хооронд бүх анхны тоог хэвлэ

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `missing return statement` | `int` буцаах method-д `return` байхгүй | `return x;` нэмэх |
| `incompatible types: void cannot be converted to int` | `void` method-ын үр дүнг хадгалахыг оролдсон | `void`-г `int` болго эсвэл утгыг хэрэглэхгүй |
| `cannot find symbol: method add` | Method-г зарлаагүй эсвэл өөр class-д байна | Method-г нэмэх, эсвэл `ClassName.add(...)` |
| Parameter нэр таарахгүй | Дуудахдаа яг тэр нэрээр дамжуулна гэж бодсон | Parameter-ын нэр зөвхөн method дотор чухал |
| Infinite recursion | Method өөрийгөө зогсолтгүй дуудсан | Base case нэмэх `if (...) return;` |

---

**Дараагийн долоо хоног:** Array & Loop — [Week 4](../week-04-array/)
