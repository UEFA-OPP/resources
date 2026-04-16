# Week 11 — Abstraction

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab11-abstraction](../../../../lab11-abstraction)

**Нэг өгүүлбэрээр:** Abstraction бол хэрэгцээт функционалын гадаад төрхийг (WHAT) зарлаж, дотоод хэрэгжүүлэлтийг (HOW) child class-д үлдээх арга — Java-д `abstract class` болон `interface`-ээр хийнэ.

---

## 🎯 Энэ долоо хоногт сурах

1. `abstract class` — хэсэгчилсэн хэрэгжүүлэлт + `abstract` method
2. `interface` — зөвхөн contract, default/static method
3. `abstract class` vs `interface` — хэзээ аль нь зөв вэ?
4. Олон interface implement хийх (`implements A, B, C`)

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Abstract Classes](https://www.youtube.com/watch?v=wl6TQVw3kzI) | 7 мин | 🟢 Эхлэгч |
| [Coding with John — Interfaces vs Abstract Classes](https://www.youtube.com/watch?v=HvPlEJ3LHgE) | 12 мин | 🟡 Дунд |
| [Telusko — Abstract Class in Java](https://www.youtube.com/watch?v=_bVCh1csrI8) | 9 мин | 🟢 Эхлэгч |
| [Java Brains — Interfaces](https://www.youtube.com/@Java.Brains/search?query=interface) | 14 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Abstract Methods and Classes](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html) — албан ёсны
- [Baeldung — Abstract Class vs Interface](https://www.baeldung.com/java-abstract-class) — харьцуулалт
- [GeeksForGeeks — Abstraction in Java](https://www.geeksforgeeks.org/abstraction-in-java-2/) — жишээтэй
- [Refactoring.Guru — Strategy Pattern](https://refactoring.guru/design-patterns/strategy) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Abstract Class](https://www.hackerrank.com/challenges/java-abstract-class/problem)
- [Exercism — Phone Number (Java)](https://exercism.org/tracks/java/exercises/phone-number) — interface хэрэглээ
- [HyperSkill — Abstract class topic](https://hyperskill.org/learn/topic/2115)

---

## 💡 Code жишээ

**❌ Муу (бүх skill-ийг нэг `if/switch`-д хийсэн):**
```java
public class SkillHandler {
    public void cast(String skillName, Character c, Character target) {
        if (skillName.equals("Fireball")) {
            target.takeDamage(50);
        } else if (skillName.equals("Heal")) {
            c.heal(30);
        } else if (skillName.equals("Stealth")) {
            c.setHidden(true);
        }
        // Шинэ skill нэмэх бүрт энэ class-ыг зас
    }
}
```

**✅ Сайн (`Skill` interface + concrete класс):**
```java
public interface Skill {
    String getName();
    int getManaCost();
    void cast(Character caster, Character target);
}

public class Fireball implements Skill {
    public String getName() { return "Fireball"; }
    public int getManaCost() { return 20; }
    public void cast(Character caster, Character target) {
        target.takeDamage(50);
    }
}

public class Heal implements Skill {
    public String getName() { return "Heal"; }
    public int getManaCost() { return 15; }
    public void cast(Character caster, Character target) {
        caster.heal(30);
    }
}

public class Stealth implements Skill {
    public String getName() { return "Stealth"; }
    public int getManaCost() { return 10; }
    public void cast(Character caster, Character target) {
        caster.setHidden(true);
    }
}

// Хэрэглэх
Skill[] skills = { new Fireball(), new Heal(), new Stealth() };
for (Skill s : skills) {
    System.out.println(s.getName() + " costs " + s.getManaCost());
}
```

Ялгаа:
- `Skill` interface нь "юу хийх ёстой" гэдгийг зарлана
- Шинэ skill нэмэх — шинэ class үүсгэхэд л хангалттай
- Handler class-аа заах шаардлагагүй
- Open/Closed principle-ийг биелүүлж байна

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `abstract class`-ээс object үүсгэж болох уу? Яагаад?
2. Interface-д field байх уу? (Hint: `public static final`)
3. `default` method interface-д яагаад нэмэгдсэн вэ?
4. Нэг class `extends` олон, `implements` олон — хязгаар юу вэ?
5. Хэзээ `abstract class`, хэзээ `interface` сонгох вэ?

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 232 — Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/) — interface хэрэгжүүлэлт
- HackerRank — "Java Interface" (interface + polymorphism)

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `Fireball is not abstract and does not override abstract method` | Interface method implement хийгээгүй | Бүх method-ыг `@Override` хийх |
| `cannot instantiate abstract class` | `new Skill()` оролдсон | Concrete subclass ашиглах |
| `interface methods cannot have body` | Interface-д `default` ашиглаагүй | `default` keyword нэмэх |
| `interface expected` | `extends Skill` гэсэн | `implements Skill` болгох |
| Олон abstract parent ашигласан | Java multiple inheritance зөвшөөрөхгүй | Interface-ээр солих |

---

**Дараагийн долоо хоног:** Exception Handling — [Week 12](../week-12-exceptions/)
