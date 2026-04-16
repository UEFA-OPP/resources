# 🧪 JUnit Basics — Тестийн үндэс

← [Home](../home/) | [Repo](../../)

Lab-ууд нь JUnit 5-р шалгагдана. Тест **унших, ажиллуулах, алдаа засах** чадвар хэрэгтэй.

---

## Тест гэж юу вэ?

Тест гэдэг нь **таны кодыг автоматаар шалгах жижиг програм**. Жишээ нь:

```java
@Test
void testTakeDamageReducesHp() {
    Character hero = new Character("Bob");  // setup
    hero.takeDamage(30);                    // act
    assertEquals(70, hero.getHp());         // assert — 70 байх ёстой
}
```

Хэрэв `hero.getHp()` нь 70 биш юм бол test `fail` болно — та юу буруу хийснийг харна.

---

## Тест ажиллуулах аргууд

### 1️⃣ Script-р (хамгийн хялбар)

```bash
bash scripts/run_tests.sh
```

Гарах жишээ:
```
━━━━━━━━━━━━━━━━━━━━━━━
  Lab 6: Character
━━━━━━━━━━━━━━━━━━━━━━━
[1/2] Компайл...   ✓
[2/2] Тест...       ✓ 8/10 passed

PASSED:
  ✓ testTakeDamageReducesHp
  ✓ testHealCannotExceedMaxHp
  ...
FAILED:
  ✗ testSpendGoldInsufficient — expected false but was true
  ✗ testNameIsFinal — ...
```

### 2️⃣ IntelliJ-д шууд
- `tests/CharacterTest.java`-г нээнэ
- Class нэрийн хажууд ногоон ▶ товч → **Run 'CharacterTest'**
- IntelliJ-ийн Run паналд үр дүн гарна

### 3️⃣ GitHub CI автоматаар
Push хийсэн тэр даруй Actions таб дээр тест ажиллаад дүн өгнө. Хялбар, гэхдээ 2–3 минут хүлээнэ.

---

## Тестийг унших — 3 хэсэг (AAA pattern)

```java
@Test
void testSpendGoldInsufficient() {
    // 1. Arrange (setup) — юу бэлдэх вэ?
    Character hero = new Character("Bob");
    hero.earnGold(50);

    // 2. Act — юу хийх вэ?
    boolean result = hero.spendGold(100);

    // 3. Assert — ямар үр дүн байх ёстой вэ?
    assertFalse(result);              // mөнгө хүрэлцэхгүй → false
    assertEquals(50, hero.getGold()); // мөнгө хасагдаагүй байх ёстой
}
```

**Тест нэр нь юу хийж байгааг шууд хэлдэг:**
- `testSpendGold_Insufficient` → "spendGold method-ийг хангалтгүй мөнгөтэй үед шалгана"
- `testHealCannotExceedMaxHp` → "heal хийхэд maxHp-аас хэтрэхгүй байх ёстой"

---

## Нийтлэг assertion-ууд

| Assertion | Шалгах | Жишээ |
|---|---|---|
| `assertEquals(expected, actual)` | Тэнцүү эсэх | `assertEquals(100, hero.getHp())` |
| `assertTrue(condition)` | true эсэх | `assertTrue(hero.isAlive())` |
| `assertFalse(condition)` | false эсэх | `assertFalse(hero.isDead())` |
| `assertNull(value)` | null эсэх | `assertNull(hero.getPet())` |
| `assertNotNull(value)` | null биш эсэх | `assertNotNull(hero.getName())` |
| `assertThrows(Ex.class, () -> ...)` | Exception шидэх эсэх | `assertThrows(IllegalArgumentException.class, () -> hero.takeDamage(-5))` |

---

## Алдааны мессеж унших

Тест `fail` болсон жишээ:
```
org.opentest4j.AssertionFailedError:
Expected :70
Actual   :100
  at CharacterTest.testTakeDamageReducesHp(CharacterTest.java:15)
```

Уншиж ойлгох:
- **Expected 70** — тест таны кодоос `70` ирэхийг хүлээж байна
- **Actual 100** — харин таны код `100` буцаасан
- **CharacterTest.java:15** — аль мөрөнд унссан
- **Анализ:** `takeDamage(30)` ажиллаагүй байна — `hp` хэвээр 100

---

## Локал тест бүтэлгүйтсэн бол

1. **Тест мессежийг анхааралтай унш** — expected vs actual
2. **Алдаа зураг аваад** (screenshot) тэмдэглэж ав
3. **IntelliJ debugger** ашиглан breakpoint тавьж мөр мөрөөр ажиллуул
   → [Debugging Tips](../debugging/)
4. Ойлгохгүй бол **Discussions** таб дээр асуу эсвэл багшид хандана

---

## 📺 Санал болгох видео

- [JUnit 5 in 10 minutes](https://www.youtube.com/watch?v=flpmSXVTqBI)
- [Reading a Java stack trace](https://www.youtube.com/watch?v=UEYzAzmIY-A)

---

## 🎯 Дадлага

- [JUnit 5 official guide](https://junit.org/junit5/docs/current/user-guide/)
- [Exercism — тест унших дадлага](https://exercism.org/tracks/java) — бүх дасгал тесттэй ирдэг

---

**Санамж:** Тест бол таны дайсан биш, найз чинь. Тест fail болгоод хэдэн минут зарцуулснаар үр дүнд хүрэх нь, багшийн гар шалгалтын дараа буруу болж байна гэж мэдсэнээс **маш хэд дахин хурдан**.
