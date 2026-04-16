# 🐛 Debugging Tips

← [Home](../home/) | [Repo](../../)

Алдаа гарах бол програмчлалын **байгалийн** хэсэг. Сурах зүйл нь алдаа гаргахгүй байх биш, харин **хурдан олж засах**.

---

## 📋 Алдааны 3 үндсэн төрөл

| Төрөл | Хэзээ гардаг | Жишээ |
|---|---|---|
| **Compile error** | Компайл хийх үед | `';' expected`, `cannot find symbol` |
| **Runtime error** | Ажиллах үед | `NullPointerException`, `ArrayIndexOutOfBounds` |
| **Logic error** | Програм ажиллана, гэхдээ буруу үр дүн | Тест `fail` болно |

---

## 1️⃣ Compile Error — Ямар мөрөнд ямар алдаа

### `cannot find symbol`
```
error: cannot find symbol
    hero.takeDamge(10);
        ^
  symbol:   method takeDamge(int)
```
👉 **Method-ийн нэрийг буруу бичсэн.** `takeDamage` байх ёстой. Spell checker.

### `';' expected`
```
error: ';' expected
    hero.takeDamage(10)
                       ^
```
👉 Мөрийн төгсгөлд `;` мартсан.

### `class X is public, should be declared in a file named X.java`
```
error: class Character is public, should be declared in a file named Character.java
```
👉 Класс нэр нь файл нэртэй яг тохирохгүй байна (case-sensitive).

### `incompatible types`
```
error: incompatible types: String cannot be converted to int
    int hp = "100";
```
👉 Буруу төрөл. Quote хассан уу, эсвэл `Integer.parseInt()` хэрэгтэй.

---

## 2️⃣ Runtime Error — Stack Trace унших

```
Exception in thread "main" java.lang.NullPointerException:
    Cannot invoke "Character.getHp()" because "hero" is null
    at Main.main(Main.java:12)
```

Уншиж тайлах:
- **Exception type:** `NullPointerException` — null дээр method дуудсан
- **Шалтгаан:** `hero` нь null
- **Газар:** `Main.java`-ийн 12-р мөр
- **Шийдэл:** `hero = new Character(...)` гэж үүсгээгүй байсан бололтой

### Нийтлэг runtime errors

| Error | Шалтгаан | Шийдэл |
|---|---|---|
| `NullPointerException` | null дээр method дуудсан | Обьект үүсгэсэн эсэхийг шалга |
| `ArrayIndexOutOfBoundsException: 3` | Байхгүй index-д хандсан | `< arr.length` шалгах |
| `NumberFormatException` | Integer.parseInt("abc") | Input валидаци |
| `ClassCastException` | Буруу cast хийсэн | `instanceof` шалгах |
| `StackOverflowError` | Recursion тэр чигээрээ үргэлжилсэн | Base case нэм |

---

## 3️⃣ Logic Error — Тест fail болсон бол

**Хамгийн түгээмэл шалтгаан:**

1. **Edge case орхигдсон** — сөрөг утга, 0, max утга
2. **Off-by-one алдаа** — `<` vs `<=`, `i < n` vs `i <= n`
3. **Буруу оператор** — `=` vs `==`, `&` vs `&&`
4. **Shadow variable** — параметрийг field гэж андуурсан (`this.x` мартсан)

### Жишээ — Off-by-one

❌ Алдаатай:
```java
public void takeDamage(int amount) {
    hp = hp - amount;  // hp сөрөг болж чадна!
}
```

✅ Зөв:
```java
public void takeDamage(int amount) {
    hp = Math.max(0, hp - amount);
}
```

### Жишээ — Shadow variable

❌ Алдаатай:
```java
public void setName(String name) {
    name = name;  // параметрээ өөр лүүгээ оноож байна, field-д хүрэхгүй
}
```

✅ Зөв:
```java
public void setName(String name) {
    this.name = name;
}
```

---

## 🔍 IntelliJ Debugger — Хамгийн хүчирхэг арга

1. Мөрийн дугаарын хажууд **цэг дарж** breakpoint тавина (улаан цэгцэнд болно)
2. ▶ товчний оронд **🐞 Debug** товч дарна
3. Програм таны breakpoint-д зогсоно
4. **Variables** паналд бүх хувьсагчийн одоогийн утгыг харна
5. Toolbar дээрх товчнууд:
   - **F8** (Step Over) — дараагийн мөрөнд шилжих
   - **F7** (Step Into) — method дотор орох
   - **Shift+F8** (Step Out) — method-ээс гарах
   - **F9** (Resume) — дараагийн breakpoint хүртэл ажиллуулах

**Үр дүнтэй арга:**
1. Тест fail болсон мөрний **assert** дээр breakpoint тавина
2. Test-ийг debug mode-д ажиллуулна (🐞 товч)
3. Тухайн мөрөнд зогссоны дараа хувьсагчдын утга хараад, хаана буруу болсныг олно

---

## 🐛 "Rubber duck" debugging

Шийдэл олохгүй үед — нохой, муур, нөхөрт **чангаар тайлбарлана**.

> "Миний `takeDamage` method `hp = hp - amount` хийж байгаа. Expected 70, actual 100. Гэхдээ `amount = 30`, `hp = 100`. Яагаад..."

Тайлбарлах явцад ихэвчлэн өөрөө л шийдлийг олдог.

---

## 📞 Тусламж гуйх стратеги

Багшид эсвэл Discussions-д асуухдаа **дараах 4-ийг заавал оруулна**:

1. **Юу хийж байсан** (lab 6, `takeDamage` method)
2. **Юу ожидал** (expected: 70)
3. **Юу болсон** (actual: 100, тест лог хавсарга)
4. **Юу хийж үзсэн** (google хийсэн, x variant-ыг туршсан)

Ингэснээр багш **30 секундэд** шалтгааныг олно, мөн та `debugging` чадвараа харуулсанд уг мессеж илүү сайн хариулт авна.

---

## 📺 Санал болгох видео

- [How to read a Java stack trace](https://www.youtube.com/watch?v=UEYzAzmIY-A)
- [IntelliJ Debugger tutorial](https://www.youtube.com/watch?v=d4qcC0V3ULg)
- [Rubber duck debugging explained](https://rubberduckdebugging.com/)

---

**Эцэст нь:** алдаа гарах бүр өөрийгөө "би чадахгүй" гэж бодохгүй. Алдаа бол **сурах хамгийн хурдан арга**.
