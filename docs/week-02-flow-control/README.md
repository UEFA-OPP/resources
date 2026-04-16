# Week 2 — Variable & Flow Control

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab2-flow-control](../../../../lab2-flow-control)

**Нэг өгүүлбэрээр:** Program гэдэг бол өгөгдлийг хадгалах (variable), шалгах (if/else), давтах (for/while) 3 үндсэн үйлдлийн нийлбэр — энэ 3-ийг эзэмшвэл та юу ч бичиж чадна.

---

## 🎯 Энэ долоо хоногт сурах

1. Primitive data type-ууд: `int`, `double`, `boolean`, `char`, `String`
2. Operator: `+ - * / %`, харьцуулалт `== != < >`, logic `&& || !`
3. Нөхцөлт илэрхийлэл: `if / else if / else`, `switch`
4. Loop: `for`, `while`, `do-while` — ямар үед алийг нь хэрэглэх вэ?

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java Variables & Data Types](https://www.youtube.com/watch?v=OUTqKkERO64) | 14 мин | 🟢 Эхлэгч |
| [Bro Code — Java if statements](https://www.youtube.com/watch?v=_six4dC5RQA) | 10 мин | 🟢 Эхлэгч |
| [Coding with John — For loops vs While loops](https://www.youtube.com/@CodingWithJohn/search?query=for+loop) | 9 мин | 🟢 Эхлэгч |
| [Neso Academy — Operators in Java](https://www.youtube.com/@nesoacademy/search?query=java+operators) | 15 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеог үзэж, IntelliJ дээр хамт туршаарай.

---

## 📖 Унших

- [Oracle — Language Basics (Variables)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html) — албан ёсны
- [W3Schools — Java Data Types](https://www.w3schools.com/java/java_data_types.asp) — цэвэрхэн хүснэгт
- [Baeldung — Control Structures in Java](https://www.baeldung.com/java-control-structures) — хамгийн бүрэн
- [GeeksForGeeks — Loops in Java](https://www.geeksforgeeks.org/loops-in-java/) — жишээтэй

---

## 🎮 Интерактив дадлага

- [HackerRank — Java If-Else](https://www.hackerrank.com/challenges/java-if-else/problem) — анхны нөхцөл дасгал
- [HackerRank — Java Loops I](https://www.hackerrank.com/challenges/java-loops/problem) — үржих үйлдэл давтах
- [Exercism — Leap (Java)](https://exercism.org/tracks/java/exercises/leap) — if-ээр leap year тооцох

---

## 💡 Code жишээ

**Нас шалгагч — variable, if/else, loop бүгд хамт:**
```java
public class AgeChecker {
    public static void main(String[] args) {
        int[] ages = {12, 17, 18, 25, 67};

        for (int age : ages) {
            if (age < 18) {
                System.out.println(age + ": too young");
            } else if (age < 65) {
                System.out.println(age + ": adult");
            } else {
                System.out.println(age + ": senior");
            }
        }
    }
}
```

Тайлбар:
- `int[] ages` — хэд хэдэн тоог нэг хувьсагчид хийж байна (Week 4-д илүү дэлгэрэнгүй)
- `for (int age : ages)` — **for-each** loop, array бүрийн элемент дээр явна
- `if / else if / else` — нөхцөлийг **дарааллаар** шалгана, эхнийх нь үнэн бол дараахыг хардаггүй

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `int` ба `double`-ын ялгаа юу вэ? `5 / 2` нь 2.5 биш 2 болох шалтгаан?
2. `=` ба `==`-ийн ялгаа? Хэзээ алийг нь ашигладаг вэ?
3. `for` ба `while`-ийг хэзээ сонгох вэ? Ямар үед `do-while` ашигтай вэ?
4. `&&` ба `||`-ийн short-circuit evaluation гэж юу вэ?
5. `switch`-ийг `if/else if`-ээр бүрэн орлуулж болох уу? Хэзээ `switch` нь илүү цэвэр вэ?

---

## 🏆 Challenge

- HackerRank — "Java Loops II" — arithmetic series-ийн дасгал
- FizzBuzz — 1-100 хүртэл: 3-д хуваагдвал Fizz, 5-д Buzz, 15-д FizzBuzz

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `cannot find symbol: x` | Variable зарлахаасаа өмнө хэрэглэсэн | Эхлээд `int x = 0;` зарла |
| `incompatible types: String cannot be converted to int` | `String`-г `int`-д шууд хийсэн | `Integer.parseInt(s)` ашигла |
| Infinite loop (stuck) | `while` нөхцөл хэзээ ч false болохгүй | `i++` гэх мэт өөрчлөлтийг дотор нь бич |
| `if (x = 5)` — compile error | `=` assignment, `==` харьцуулах | `if (x == 5)` зөв |
| `5 / 2 = 2` (2.5 биш) | Integer division | Нэгийг нь `double` болго: `5.0 / 2` |

---

**Дараагийн долоо хоног:** Method & Code Reuse — [Week 3](../week-03-method/)
