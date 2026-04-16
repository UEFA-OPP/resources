# Week 6 — Encapsulation

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab6-encapsulation](../../../../lab6-encapsulation)

**Нэг өгүүлбэрээр:** Encapsulation гэдэг нь class-ийн дотоод өгөгдлийг (field) гаднаас шууд хандахаас хамгаалж, зөвхөн тодорхой method-оор хандуулах зарчим.

---

## 🎯 Энэ долоо хоногт сурах

1. `private` keyword-ийн утга
2. Getter / Setter-ийн зорилго
3. Validation — сөрөг эсвэл буруу утга blockchain хийх
4. Information hiding-ийн давуу тал

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Encapsulation in Java](https://www.youtube.com/watch?v=NVSIqZq9TVU) | 6 мин | 🟢 Эхлэгч |
| [Derek Banas — Java Encapsulation](https://www.youtube.com/watch?v=EJNbr6wGu9s) | 8 мин | 🟢 Эхлэгч |
| [Neso Academy — Encapsulation Explained](https://www.youtube.com/watch?v=vcGWRIMRdBM) | 12 мин | 🟡 Дунд |
| [Telusko — OOP Encapsulation](https://www.youtube.com/watch?v=lYn_7cpxM7U) | 10 мин | 🟢 Эхлэгч |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Controlling Access to Class Members](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html) — албан ёсны
- [Baeldung — Encapsulation](https://www.baeldung.com/java-encapsulation) — жишээтэй
- [GeeksForGeeks — Encapsulation](https://www.geeksforgeeks.org/encapsulation-in-java/) — олон дасгал
- [Refactoring.Guru — Encapsulate Field](https://refactoring.guru/encapsulate-field) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Access Modifiers](https://www.hackerrank.com/domains/java) — Introduction → Access Modifiers
- [Exercism — Secret Handshake (Java)](https://exercism.org/tracks/java/exercises/secret-handshake)
- [HyperSkill — Encapsulation topic](https://hyperskill.org/learn/topic/2247)

---

## 💡 Code жишээ

**❌ Муу (public field):**
```java
public class Account {
    public int balance;
}

Account a = new Account();
a.balance = -5000;  // Ямар ч шалгалтгүй, балансыг сөрөг болгочихож байна
```

**✅ Сайн (encapsulated):**
```java
public class Account {
    private int balance;

    public int getBalance() {
        return balance;
    }

    public void deposit(int amount) {
        if (amount <= 0) {
            return; // эсвэл exception throw
        }
        balance += amount;
    }

    public boolean withdraw(int amount) {
        if (amount <= 0 || amount > balance) {
            return false;
        }
        balance -= amount;
        return true;
    }
}
```

Ялгаа:
- `balance` нь `private` — гаднаас шууд өөрчлөгдөхгүй
- `deposit` сөрөг утга хүлээж авахгүй
- `withdraw` хангалттай мөнгө байгаа эсэхийг шалгана

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `private` ба `public` field-ийн ялгаа юу вэ?
2. Яагаад `balance`-г `public` болговол аюултай вэ?
3. Getter байгаа ч setter байхгүй field байж болох уу? (Hint: final + constructor)
4. Validation-ыг setter дотор хийх vs constructor дотор хийх — ялгаа?
5. `toString()` override хийхэд encapsulation-д хор учруулах уу?

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 1603 — Design Parking System](https://leetcode.com/problems/design-parking-system/) — энгийн encapsulation жишээ
- HackerRank — "Java BitSet" (encapsulation + bit operations)

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `balance has private access` | Өөр class-аас шууд хандсан | Getter ашиглах |
| Getter байхгүй | Зарлаагүй | `public int getBalance()` нэмнэ |
| Setter нь validation хийхгүй | `this.x = x` шууд | `if` нэмж шалга |
| `takeDamage(-10)` HP нэмчихэж байна | Сөрөг утга шалгаагүй | `if (amount < 0) return;` |

---

**Дараагийн долоо хоног:** Constructor — [Week 7](../week-07-constructor/) *(coming soon)*
