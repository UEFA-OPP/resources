# Week 5 — Class & Object

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab5-class-object](../../../../lab5-class-object)

**Нэг өгүүлбэрээр:** Class бол "зураг төсөл" (blueprint), object бол түүгээр хийсэн **жинхэнэ бодит зүйл** — энэ долоо хоногоос эхлэн та процедурын сэтгэлгээнээс OOP-ийн сэтгэлгээнд шилжиж, Week 6-ээс эхлэх **Dungeon of OOP** цувралын босгон дээр зогсоно.

---

## 🎯 Энэ долоо хоногт сурах

1. Class зарлах, field (state) ба method (behavior) тодорхойлох
2. `new` keyword-ээр object үүсгэх, ижил class-аас **олон** object гаргах
3. `this` keyword — object өөрийгөө заах
4. Бодит ертөнцийн зүйлийг class болгож модел хийх (Student, Car, BankAccount)

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java classes and objects](https://www.youtube.com/watch?v=Iz-NhRQEvnc) | 12 мин | 🟢 Эхлэгч |
| [Coding with John — Classes and Objects](https://www.youtube.com/@CodingWithJohn/search?query=classes+objects) | 15 мин | 🟢 Эхлэгч |
| [Telusko — Class and Object in Java](https://www.youtube.com/@Telusko/search?query=class+object) | 10 мин | 🟢 Эхлэгч |
| [Derek Banas — Java Classes](https://www.youtube.com/@derekbanas/search?query=java+class) | 14 мин | 🟡 Дунд |

**Хамгийн бага:** Bro Code-ийн видеог үзэж, Student class-аа өөрөө бич.

---

## 📖 Унших

- [Oracle — Classes and Objects](https://docs.oracle.com/javase/tutorial/java/javaOO/classes.html) — албан ёсны
- [W3Schools — Java Classes/Objects](https://www.w3schools.com/java/java_classes.asp) — богино, ойлгомжтой
- [Baeldung — Java Class](https://www.baeldung.com/java-classes-objects) — бүрэн хэмжээний
- [GeeksForGeeks — Classes and Objects](https://www.geeksforgeeks.org/classes-objects-java/) — жишээ баялаг

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Classes](https://www.hackerrank.com/domains/java) — Introduction → Classes
- [Exercism — Lasagna (Java)](https://exercism.org/tracks/java/exercises/lasagna) — анхны class
- [HyperSkill — Class basics](https://hyperskill.org/learn/topic/1727) — интерактив

---

## 💡 Code жишээ

**Student class — процедураас OOP руу шилжилт:**
```java
public class Student {
    String name;
    int age;
    double gpa;

    public void introduce() {
        System.out.println("Hi, I am " + name + ", age " + age + ", GPA " + gpa);
    }

    public boolean isHonorStudent() {
        return gpa >= 3.5;
    }
}
```

**Main дотроос ашиглах:**
```java
public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.name = "Bat";
        s1.age = 20;
        s1.gpa = 3.8;

        Student s2 = new Student();
        s2.name = "Sara";
        s2.age = 19;
        s2.gpa = 3.2;

        s1.introduce();
        s2.introduce();

        System.out.println(s1.name + " honor? " + s1.isHonorStudent());
        System.out.println(s2.name + " honor? " + s2.isHonorStudent());
    }
}
```

Тайлбар:
- `Student` class — **зураг төсөл**, өөрөө хэнийг ч илэрхийлэхгүй
- `s1`, `s2` — **object** буюу жинхэнэ оюутан, тус бүр өөрийн `name`, `age`-тэй
- `new Student()` — шинэ object санах ойд үүсгэнэ
- `s1.introduce()` — тухайн object-ын өөрийн өгөгдлөөр ажиллана

> ⚠️ **Week 6 preview:** `name`, `age`, `gpa`-г `public` байдлаар гаднаас шууд өөрчилж болж байгаа нь **асуудалтай** (нас сөрөг, GPA 999 гэх мэт). Дараагийн долоо хоногт `private` болгож, encapsulation хийнэ.

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. Class ба object-ын ялгаа юу вэ? Нэг class-аас олон object гаргах уу?
2. `new` keyword яг юу хийж байгаа вэ (санах ой тал)?
3. `this.name = name;` гэж яагаад бичих шаардлагатай вэ?
4. Field-д default утга байдаг уу? `int`, `String`, `boolean` тус бүрт?
5. `static` field ба instance field-ын ялгаа?

---

## 🏆 Challenge

- `BankAccount` class бичээрэй: `balance`, `deposit()`, `withdraw()`, `getBalance()`
- `Car` class — `brand`, `speed`, `accelerate()`, `brake()` — 2 машин үүсгэж уралдуул

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `NullPointerException` | `new` хийлгүй field-д хандсан | `new ClassName()` хийх |
| `non-static cannot be referenced from static` | `main` (static) доороос instance field дуудсан | Эхлээд object үүсгэ, тэгээд `s1.field` |
| `s1 == s2` — ижил утгатай ч false | Reference харьцуулалт | `.equals()` override хийх (Week 10) |
| `this` keyword дахиад орчив | Parameter, field нэр адил | `this.name = name;` зориуд бичнэ |
| Хоёр object нэг л field-тэй юм шиг | `static` field хэрэглэсэн | `static`-г аваад шалга |

---

**Дараагийн долоо хоног — OOP эхэлж буй газар:** Encapsulation — [Week 6](../week-06-encapsulation/) ✅
