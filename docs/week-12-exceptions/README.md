# Week 12 — Exception Handling

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab12-exceptions](../../../../lab12-exceptions)

**Нэг өгүүлбэрээр:** Exception handling бол програмын явцад гарах алдааг `try/catch/finally` ашиглан засаж, системийг "crash" хийлгүйгээр зогсдог бүтэц.

---

## 🎯 Энэ долоо хоногт сурах

1. `try / catch / finally` бүтэц
2. Checked vs unchecked exception (ялгаа + хэзээ аль нь)
3. Custom exception (`InsufficientGoldException`) үүсгэх
4. `throws` vs `throw` — хэрхэн ашиглах

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java Exception Handling](https://www.youtube.com/watch?v=1XAfapkBQjk) | 12 мин | 🟢 Эхлэгч |
| [Coding with John — Exceptions Tutorial](https://www.youtube.com/watch?v=1XAfapkBQjk) | 11 мин | 🟢 Эхлэгч |
| [Telusko — Exception Handling](https://www.youtube.com/watch?v=1uwUSNkJeIY) | 10 мин | 🟢 Эхлэгч |
| [Java Brains — Checked vs Unchecked](https://www.youtube.com/@Java.Brains/search?query=exception) | 14 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Exceptions Lesson](https://docs.oracle.com/javase/tutorial/essential/exceptions/) — албан ёсны
- [Baeldung — Exception Handling](https://www.baeldung.com/java-exceptions) — жишээтэй
- [GeeksForGeeks — Exceptions in Java](https://www.geeksforgeeks.org/exceptions-in-java/) — төрлүүд
- [Refactoring.Guru — Replace Error Code with Exception](https://refactoring.guru/replace-error-code-with-exception) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Exception Handling](https://www.hackerrank.com/challenges/java-exception-handling/problem)
- [Exercism — Error Handling (Java)](https://exercism.org/tracks/java/exercises/error-handling)
- [HyperSkill — Exceptions topic](https://hyperskill.org/learn/topic/2158)

---

## 💡 Code жишээ

**❌ Муу (алдааг `return -1`-ээр илэрхийлж, дараа нь мартсан):**
```java
public int buyItem(Player p, Item item) {
    if (p.gold < item.price) {
        return -1;  // дуудсан код шалгах уу? Ихэнх нь мартана
    }
    p.gold -= item.price;
    p.addItem(item);
    return 0;
}

// Дуудлага: -1 буцахыг мартвал gold мөнгөгүй ч item авчих
buyItem(player, sword);
```

**✅ Сайн (custom exception):**
```java
public class InsufficientGoldException extends RuntimeException {
    public InsufficientGoldException(int have, int need) {
        super("Хангалттай алт алга: " + have + "/" + need);
    }
}

public class NotEnoughManaException extends RuntimeException {
    public NotEnoughManaException(int have, int need) {
        super("Хангалттай mana алга: " + have + "/" + need);
    }
}

public void buyItem(Player p, Item item) {
    if (p.getGold() < item.getPrice()) {
        throw new InsufficientGoldException(p.getGold(), item.getPrice());
    }
    p.deductGold(item.getPrice());
    p.addItem(item);
}

public void castSpell(Mage m, Spell s) {
    if (m.getMana() < s.getCost()) {
        throw new NotEnoughManaException(m.getMana(), s.getCost());
    }
    m.deductMana(s.getCost());
    s.cast();
}

// Хэрэглэх — алдааг шууд барина
try {
    buyItem(player, sword);
} catch (InsufficientGoldException e) {
    System.out.println(e.getMessage());
} finally {
    System.out.println("Дэлгүүр хаагдсан");
}
```

Ялгаа:
- Алдаа нь мессеж + context-той
- Зөв газарт барихгүй бол JVM stop хийнэ (туршилт амархан)
- `finally` нь resource цэвэрлэх газар
- Тодорхой нэртэй exception нь debug-д тусална

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. Checked exception-ыг яагаад `throws` заах шаардлагатай вэ?
2. `RuntimeException` extend хийсэн бол checked үү, unchecked уу?
3. `finally` блок хэзээ ч ажиллахгүй тохиолдол байдаг уу? (hint: `System.exit`)
4. Олон catch block-ийн дараалал ямар байх ёстой? (narrow → broad)
5. `try-with-resources` ба `finally` — ялгаа юу вэ?

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 8 — String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/) — input validation + exception style
- HackerRank — "Java Exception Handling (Try-catch)"

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `unreported exception must be caught or declared` | Checked exception handle хийгээгүй | `try/catch` эсвэл `throws` |
| `exception has already been caught` | Өмнөх `catch` block-д баригдсан | Order-ыг child → parent |
| `catch (Exception e) { }` хоосон | Алдаа нуусан | Хамгийн багадаа log бичих |
| `NullPointerException` runtime-д | `null` шалгаагүй | `Objects.requireNonNull(...)` |
| `throw` ба `throws` нэг гэж бодно | Нэр төстэй, утга өөр | `throw` — объект, `throws` — signature |

---

**Дараагийн долоо хоног:** Collections — [Week 13](../week-13-collections/)
