# Week 9 — Inheritance

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab9-inheritance](../../../../lab9-inheritance)

**Нэг өгүүлбэрээр:** Inheritance бол нэг class өөр class-ийн field болон method-ыг өвлөн авч, шинэ онцлог нэмэх OOP-ийн зарчим (IS-A харилцаа).

---

## 🎯 Энэ долоо хоногт сурах

1. `extends` keyword болон IS-A харилцаа
2. `super(...)` ашиглан parent constructor-ыг дуудах
3. `protected` access modifier — child class-д хандах эрх
4. Code reuse — яагаад inheritance нь давхардлыг бууруулдаг

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java Inheritance](https://www.youtube.com/watch?v=hvWF1SegRt4) | 7 мин | 🟢 Эхлэгч |
| [Coding with John — Inheritance Full Tutorial](https://www.youtube.com/watch?v=Mzm33fCPJIU) | 14 мин | 🟡 Дунд |
| [Telusko — Inheritance in Java](https://www.youtube.com/watch?v=fmho72I__Bs) | 11 мин | 🟢 Эхлэгч |
| [Neso Academy — Inheritance Basics](https://www.youtube.com/@nesoacademy/search?query=java+inheritance) | 10 мин | 🟢 Эхлэгч |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Inheritance](https://docs.oracle.com/javase/tutorial/java/IandI/subclasses.html) — албан ёсны
- [Baeldung — Inheritance in Java](https://www.baeldung.com/java-inheritance) — жишээтэй
- [GeeksForGeeks — Inheritance in Java](https://www.geeksforgeeks.org/inheritance-in-java/) — төрлүүд + дасгал
- [Refactoring.Guru — Replace Inheritance with Delegation](https://refactoring.guru/replace-inheritance-with-delegation) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Inheritance I & II](https://www.hackerrank.com/challenges/java-inheritance-1/problem) — 2 шат
- [Exercism — Ledger (Java)](https://exercism.org/tracks/java/exercises/ledger) — хэрэгтэй inheritance
- [HyperSkill — Inheritance topic](https://hyperskill.org/learn/topic/2113)

---

## 💡 Code жишээ

**❌ Муу (инхеритэнсгүй давхардал):**
```java
public class Warrior {
    String name; int hp;
    void attack() { System.out.println(name + " swings sword"); }
    void takeDamage(int d) { hp -= d; }
}

public class Mage {
    String name; int hp;  // давхардсан
    void attack() { System.out.println(name + " casts spell"); }
    void takeDamage(int d) { hp -= d; } // давхардсан
}
```

**✅ Сайн (parent Character → child Warrior/Mage/Rogue):**
```java
public class Character {
    protected String name;
    protected int hp;

    public Character(String name, int hp) {
        this.name = name;
        this.hp = hp;
    }

    public void takeDamage(int damage) {
        hp -= damage;
    }

    public void attack() {
        System.out.println(name + " attacks");
    }
}

public class Warrior extends Character {
    private int armor;

    public Warrior(String name, int armor) {
        super(name, 150);      // parent constructor
        this.armor = armor;
    }

    @Override
    public void takeDamage(int damage) {
        super.takeDamage(Math.max(0, damage - armor)); // armor буурна
    }
}

public class Mage extends Character {
    public Mage(String name) {
        super(name, 80);
    }
}
```

Ялгаа:
- `Character` нь нийтлэг field/method-ыг нэг дор хадгална
- `super(...)` нь parent-ийн constructor-ыг дуудна
- `Warrior` нь `takeDamage`-ыг өөрөө өргөтгөж, `super.takeDamage(...)`-ыг дуудсан
- `protected` нь child class-аас хандах боломж олгоно

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. Java-д олон parent class-аас inherit хийж болох уу? (multiple inheritance)
2. `super()` ба `this()` — хоёуланг нь нэг constructor-д дуудаж болох уу?
3. `private` field child class-д хандах уу? Яагаад?
4. IS-A vs HAS-A — ямар нөхцөлд аль нь зөв вэ?
5. Хэрэв child class `super(...)` дуудаагүй бол юу болдог вэ?

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 146 — LRU Cache](https://leetcode.com/problems/lru-cache/) — `LinkedHashMap` extend хийх боломжтой
- HackerRank — "Java Abstract Class" (abstract parent + concrete child)

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `cannot find symbol: super(...)` | Parent-д тохирох constructor байхгүй | Parent-д overload нэмэх эсвэл зөв arg дамжуулах |
| `name has private access in Character` | parent field `private` байна | `protected` болгох эсвэл getter нэмэх |
| `constructor Character in class Character cannot be applied` | `super()` arg буруу | `super(name, hp)` зөв дамжуулах |
| Child class бүгдийг дахин бичнэ | `extends` хэрэглээгүй | `class Warrior extends Character` |
| Diamond problem | Олон inheritance оролдсон | Interface ашиглах |

---

**Дараагийн долоо хоног:** Polymorphism — [Week 10](../week-10-polymorphism/)
