# Week 1 — Java суурь + OOP сэтгэлгээ

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab1-hello-java](../../../../lab1-hello-java)

**Нэг өгүүлбэрээр:** Java хэл бол класс-д суурилсан, компьютерт "юу хийхийг" биш "юу байхыг" зааж өгдөг программчлалын хэл — энэ долоо хоногт бид IntelliJ-гээ суулгаж, анхны `Hello World`-оо ажиллуулна.

---

## 🎯 Энэ долоо хоногт сурах

1. JDK болон IntelliJ IDEA-г өөрийн компьютерт суулгах
2. `public static void main(String[] args)`-ийн бүтэц, утга
3. `System.out.println(...)`-ээр текст хэвлэх, `//` comment бичих
4. Анхны compile error-ийг уншиж ойлгох (missing semicolon, wrong class name)

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java Tutorial for Beginners (first 20 min)](https://www.youtube.com/watch?v=xk4_1vDrzzo) | 20 мин | 🟢 Эхлэгч |
| [Amigoscode — Install IntelliJ IDEA + JDK](https://www.youtube.com/@amigoscode/search?query=intellij+java) | 10 мин | 🟢 Эхлэгч |
| [mooc.fi — Java Programming MOOC trailer](https://www.youtube.com/@moocfi/search?query=java) | 8 мин | 🟢 Эхлэгч |
| [Telusko — Why Java?](https://www.youtube.com/@Telusko/search?query=why+java) | 12 мин | 🟢 Эхлэгч |

**Хамгийн бага:** Bro Code-ийн эхний 20 минутыг үзэж, IntelliJ-дээ хамт бичээрэй.

---

## 📖 Унших

- [Oracle — Getting Started with Java](https://docs.oracle.com/javase/tutorial/getStarted/index.html) — албан ёсны гарын авлага
- [W3Schools — Java Introduction](https://www.w3schools.com/java/java_intro.asp) — товч, тодорхой
- [GeeksForGeeks — First Java Program](https://www.geeksforgeeks.org/java-hello-world-program/) — алхам алхмаар
- [Baeldung — The Java main Method](https://www.baeldung.com/java-main-method) — `main()`-ийн гүн гүнзгий

---

## 🎮 Интерактив дадлага

- [HackerRank — Welcome to Java!](https://www.hackerrank.com/challenges/welcome-to-java/problem) — хамгийн анхны дасгал
- [Codecademy — Learn Java (Hello World unit)](https://www.codecademy.com/learn/learn-java) — нэг цуврал
- [HyperSkill — Introduction to Java](https://hyperskill.org/tracks/1) — track эхлэх

---

## 💡 Code жишээ

**1-р алхам — хамгийн энгийн:**
```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Sain baina uu, UEFA!");
    }
}
```

**2-р алхам — хэдэн мөр, comment нэмэх:**
```java
public class Hello {
    public static void main(String[] args) {
        // Tavtai morilno uu — ene bol minii anhnii Java program
        System.out.println("Sain baina uu!");
        System.out.println("Minii ner ___ .");
        System.out.println("UEFA-iin OOP hicheel ehelj baina.");
    }
}
```

Тайлбар:
- `public class Hello` — файлын нэр **яг** `Hello.java` байна
- `main(...)` — JVM энэ method-ыг эхлээд дуудана
- `System.out.println(...)` — текст хэвлэж, шинэ мөр үүсгэнэ
- `//` — нэг мөрийн comment — компьютер уншихгүй, хүн уншина

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. Яагаад Java файлын нэр class-ийн нэртэй **яг** тохирох ёстой вэ?
2. `println` ба `print`-ийн ялгаа юу вэ?
3. `main` method-ын `String[] args` нь юуг илэрхийлэх вэ?
4. `;` тавихаа мартвал ямар алдаа гарах вэ? Яаж засах вэ?
5. JDK, JRE, JVM — эдгээрийн ялгаа?

---

## 🏆 Challenge

- HackerRank — "Java Stdin and Stdout I" — Scanner-ээр оролт авах
- IntelliJ-дээ 3 өөр `.java` файл үүсгэж, тус бүрд нь өөр мэссэж хэвлүүл

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `class Hello is public, should be declared in a file named Hello.java` | Файлын нэр class-тай таарахгүй | Файлыг `Hello.java` нэртэй болгох |
| `';' expected` | Мөр төгсгөлд `;` байхгүй | Мөрийн сүүлд `;` нэм |
| `cannot find symbol: Systme` | Үсэг буруу бичсэн | `System` гэж зөв бич |
| `Main method not found` | `main` method байхгүй эсвэл signature буруу | `public static void main(String[] args)` хуулж бич |
| Program ажиллахгүй | Run button дарахгүй, зөв class-ыг сонгоогүй | IntelliJ дээр green ▶ дарах |

---

**Дараагийн долоо хоног:** Variable & Flow Control — [Week 2](../week-02-flow-control/)
