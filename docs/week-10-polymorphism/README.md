# Week 10 — Polymorphism

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab10-polymorphism](../../../../lab10-polymorphism)

**Нэг өгүүлбэрээр:** Polymorphism бол нэг parent төрлийн reference-ээр өөр өөр child object-уудыг нэгэн адил ажиллуулж, method-ыг dynamic байдлаар сонгох чадвар.

---

## 🎯 Энэ долоо хоногт сурах

1. Method overriding (`@Override`) — child-ийн өөрийн хэрэгжүүлэлт
2. Dynamic (late) binding — runtime-д аль method дуудагдах нь шийдэгдэнэ
3. Upcasting — `Character c = new Warrior(...)`
4. `instanceof` + pattern matching (Java 16+)

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Polymorphism in Java](https://www.youtube.com/watch?v=jhDUxynEQRI) | 7 мин | 🟢 Эхлэгч |
| [Coding with John — Polymorphism Full Tutorial](https://www.youtube.com/watch?v=qU1JMMkzVwg) | 13 мин | 🟡 Дунд |
| [Telusko — Polymorphism Explained](https://www.youtube.com/watch?v=uFEtVz3h6SE) | 10 мин | 🟢 Эхлэгч |
| [Neso Academy — Dynamic Method Dispatch](https://www.youtube.com/@nesoacademy/search?query=java+polymorphism) | 11 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Polymorphism](https://docs.oracle.com/javase/tutorial/java/IandI/polymorphism.html) — албан ёсны
- [Baeldung — Polymorphism in Java](https://www.baeldung.com/java-polymorphism) — жишээтэй
- [GeeksForGeeks — Polymorphism](https://www.geeksforgeeks.org/polymorphism-in-java/) — compile-time vs runtime
- [Refactoring.Guru — Replace Conditional with Polymorphism](https://refactoring.guru/replace-conditional-with-polymorphism) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Inheritance II](https://www.hackerrank.com/challenges/java-inheritance-2/problem) — override дасгал
- [Exercism — Strain (Java)](https://exercism.org/tracks/java/exercises/strain) — олон төрөлтэй дасгал
- [HyperSkill — Polymorphism topic](https://hyperskill.org/learn/topic/2118)

---

## 💡 Code жишээ

**❌ Муу (`if/else` + type check):**
```java
public void fight(Character c) {
    if (c.type.equals("warrior")) {
        System.out.println("Sword slash!");
    } else if (c.type.equals("mage")) {
        System.out.println("Fireball!");
    } else if (c.type.equals("rogue")) {
        System.out.println("Backstab!");
    }
    // Шинэ class нэмэх бүрт if нэмэх хэрэгтэй
}
```

**✅ Сайн (polymorphism + override):**
```java
public class Character {
    protected String name;
    public void attack() {
        System.out.println(name + " attacks");
    }
}

public class Warrior extends Character {
    @Override
    public void attack() {
        System.out.println(name + " slashes with sword!");
    }
}

public class Mage extends Character {
    @Override
    public void attack() {
        System.out.println(name + " casts Fireball!");
    }
}

public class Rogue extends Character {
    @Override
    public void attack() {
        System.out.println(name + " backstabs!");
    }
}

// Battle system
Character[] party = { new Warrior("Thor"), new Mage("Gandalf"), new Rogue("Ezio") };
for (Character c : party) {
    c.attack();  // Runtime-д тохирох attack() дуудагдана
}
```

Ялгаа:
- Array нь `Character[]` — гэхдээ object бүр өөр child төрөлтэй
- `c.attack()` дуудахад JVM runtime-д аль класс бол мэднэ (dynamic binding)
- Шинэ `Paladin` class нэмэхэд `if` шинэчлэх хэрэггүй

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. Overriding ба overloading — ялгаа юу вэ?
2. `@Override` аннотаци яагаад хэрэгтэй вэ?
3. Upcasting хэзээ автомат, downcasting хэзээ ручной байдаг вэ?
4. `static` method overriding хийгддэг үү? (hint: shadowing)
5. `private` method-ыг override хийж болох уу?

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 589 — N-ary Tree Preorder](https://leetcode.com/problems/n-ary-tree-preorder-traversal/) — recursive polymorphism
- HackerRank — "Java Dequeue" (interface + polymorphism)

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `method does not override from its superclass` | Гарын үсэг таарахгүй | `@Override`, параметрийг шалгах |
| `ClassCastException` | Буруу downcast | `instanceof`-оор эхэлж шалгах |
| `Warrior cannot be converted to Mage` | Sibling class-ууд cast болохгүй | Parent-ээр cast хийх |
| Method дуудагдахгүй | Child class-д override хийгээгүй | `@Override` нэмээд implementation бичих |
| `static` method override гэж бодсон | `static` бол shadowing | Instance method болгох |

---

**Дараагийн долоо хоног:** Abstraction — [Week 11](../week-11-abstraction/)
