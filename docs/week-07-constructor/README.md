# Week 7 — Constructor

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab7-constructor](../../../../lab7-constructor)

**Нэг өгүүлбэрээр:** Constructor бол object үүсэх мөчид field-үүдийг зөв анхны утгаар дүүргэж, object-ийг "бэлэн" байдалд оруулдаг тусгай method.

---

## 🎯 Энэ долоо хоногт сурах

1. Constructor overloading — олон өөр гарын үсэгтэй constructor
2. `this()` ашиглан constructor chaining
3. Copy constructor — object-ийг хуулах зөв арга
4. Static factory method (`Character.createWarrior(...)`) — constructor-ийн өөр хувилбар

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java Constructors](https://www.youtube.com/watch?v=EOmBOVKBvwQ) | 8 мин | 🟢 Эхлэгч |
| [Coding with John — Constructors Tutorial](https://www.youtube.com/watch?v=vz1KVhYzOf0) | 10 мин | 🟢 Эхлэгч |
| [Telusko — Constructor in Java](https://www.youtube.com/watch?v=KevHkM8NjXE) | 9 мин | 🟢 Эхлэгч |
| [Neso Academy — Constructor Overloading](https://www.youtube.com/@nesoacademy/search?query=java+constructor) | 12 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Providing Constructors for Your Classes](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html) — албан ёсны
- [Baeldung — Java Constructors](https://www.baeldung.com/java-constructors) — жишээтэй
- [GeeksForGeeks — Constructors in Java](https://www.geeksforgeeks.org/constructors-in-java/) — overloading + chaining
- [Refactoring.Guru — Factory Method](https://refactoring.guru/design-patterns/factory-method) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Class (Constructors)](https://www.hackerrank.com/challenges/java-class/problem) — анхны constructor
- [Exercism — Matrix (Java)](https://exercism.org/tracks/java/exercises/matrix) — constructor + parse
- [HyperSkill — Constructors topic](https://hyperskill.org/learn/topic/2113)

---

## 💡 Code жишээ

**❌ Муу (constructor-гүй, шууд field-ээр утга өгч байна):**
```java
public class Character {
    public String name;
    public int hp;
    public int attack;
}

Character c = new Character();
c.name = "Ragnar";
// hp, attack-ийг мартчихвал 0 утгатай үлдэж, тоглоом эвдрэнэ
```

**✅ Сайн (overloaded + chained constructors):**
```java
public class Character {
    private final String name;
    private int hp;
    private int attack;

    // Бүрэн constructor
    public Character(String name, int hp, int attack) {
        if (name == null || name.isBlank()) {
            throw new IllegalArgumentException("name хоосон байж болохгүй");
        }
        this.name = name;
        this.hp = hp;
        this.attack = attack;
    }

    // Default утгатай constructor (chaining with this())
    public Character(String name) {
        this(name, 100, 10); // default HP, attack
    }

    // Copy constructor
    public Character(Character other) {
        this(other.name, other.hp, other.attack);
    }

    // Static factory method
    public static Character createWarrior(String name) {
        return new Character(name, 150, 15);
    }
}
```

Ялгаа:
- Object үүсэх мөчид бүх field нь зөв утгатай болно
- `this(...)` ашиглан давтагдсан кодыг арилгана
- Copy constructor нь object-ийг аюулгүй хуулна
- Static factory method нь `new` гэхээс илүү ойлгомжтой нэртэй

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. Хэрэв constructor зарлаагүй бол Java юу хийдэг вэ? (default constructor)
2. `this()` дуудалт constructor-ийн эхний мөрөнд яагаад байх ёстой вэ?
3. Overloading vs Overriding — ялгаа юу вэ?
4. Copy constructor vs `clone()` — аль нь илүү аюулгүй вэ?
5. Static factory method-ийг constructor-оос юугаараа давуу вэ? (жишээ: нэртэй)

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 1472 — Design Browser History](https://leetcode.com/problems/design-browser-history/) — constructor + state
- HackerRank — "Java Factory Pattern" (factory + constructor chain)

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `constructor Character in class Character cannot be applied to given types` | Буруу тооны argument | Overload нэмэх эсвэл default constructor ашиглах |
| `call to this must be first statement in constructor` | `this()`-ийг доор нь дуудсан | `this(...)` эхний мөрөнд байрлуулна |
| `recursive constructor invocation` | Constructor өөрийгөө дуудаж байна | Chaining-ийг шалгах |
| `final field name not initialized` | `final` field-д утга өгөөгүй | Бүх constructor-д утга өгнө |
| Copy constructor reference хуулсан | `this.list = other.list` | `new ArrayList<>(other.list)` гэж deep copy |

---

**Дараагийн долоо хоног:** Week 8 — Midterm 📝 → дараа нь Inheritance — [Week 9](../week-09-inheritance/)
