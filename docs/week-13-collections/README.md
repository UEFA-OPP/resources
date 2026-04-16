# Week 13 — Collections

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab13-collections](../../../../lab13-collections)

**Нэг өгүүлбэрээр:** Java Collections Framework бол олон element-ийг хадгалах, хайх, дараалах нийтлэг бүтэц — `List`, `Set`, `Map` гэсэн гол интерфэйстэй.

---

## 🎯 Энэ долоо хоногт сурах

1. `List` (ArrayList), `Set` (HashSet), `Map` (HashMap) — хэзээ аль нь
2. Generics (`List<Character>`) — type safety
3. Iterator болон `for-each` loop
4. `equals()` / `hashCode()` — `HashSet`, `HashMap`-д чухал

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java Collections](https://www.youtube.com/watch?v=viTHc_4XfCA) | 14 мин | 🟢 Эхлэгч |
| [Coding with John — HashMap Tutorial](https://www.youtube.com/watch?v=e0j5WQP4pbk) | 12 мин | 🟡 Дунд |
| [Telusko — Collections Framework](https://www.youtube.com/watch?v=GxkloAIfg78) | 11 мин | 🟢 Эхлэгч |
| [Amigoscode — Java Collections](https://www.youtube.com/@amigoscode/search?query=java+collections) | 16 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — Collections Trail](https://docs.oracle.com/javase/tutorial/collections/) — албан ёсны
- [Baeldung — Java Collections Overview](https://www.baeldung.com/java-collections) — бүх collection
- [GeeksForGeeks — Collections in Java](https://www.geeksforgeeks.org/collections-in-java-2/) — жишээтэй
- [Refactoring.Guru — Iterator Pattern](https://refactoring.guru/design-patterns/iterator) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java HashSet / Map](https://www.hackerrank.com/domains/java) — Data Structures branch
- [Exercism — High Scores (Java)](https://exercism.org/tracks/java/exercises/high-scores) — `List` дасгал
- [HyperSkill — Collections topic](https://hyperskill.org/learn/topic/2123)

---

## 💡 Code жишээ

**❌ Муу (array + manual бодолт):**
```java
public class Player {
    private String[] inventory = new String[100];
    private int count = 0;

    public void add(String item) {
        inventory[count++] = item;  // overflow-оос болгоомжил
    }

    public boolean hasItem(String name) {
        for (int i = 0; i < count; i++) {
            if (inventory[i].equals(name)) return true;
        }
        return false;  // O(n)
    }
}
```

**✅ Сайн (`Map` + `List` + `Set`):**
```java
import java.util.*;

public class Player {
    // Item name -> quantity
    private Map<String, Integer> inventory = new HashMap<>();

    // Party-д байгаа character-ууд (дараалал чухал)
    private List<Character> party = new ArrayList<>();

    // Аль аль нь дахин давтагдахгүй
    private Set<String> defeatedEnemies = new HashSet<>();

    public void addItem(String item, int qty) {
        inventory.merge(item, qty, Integer::sum);
    }

    public boolean hasItem(String item) {
        return inventory.containsKey(item);  // O(1)
    }

    public void defeat(String enemyName) {
        defeatedEnemies.add(enemyName);  // давхардахгүй
    }

    public void listParty() {
        for (Character c : party) {
            System.out.println(c.getName());
        }
    }
}
```

Ялгаа:
- `HashMap` — түлхүүрээр хайх O(1)
- `ArrayList` — дараалалтай, индексээр хандах
- `HashSet` — давхардах element-ыг автоматаар устгана
- Generics (`<String, Integer>`) — compile-time-д type шалгана
- Iterator `for (Character c : party)` — хялбар

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `ArrayList` ба `LinkedList` — хэзээ аль нь хурдан вэ?
2. `HashSet`-д custom object хадгалахдаа яагаад `equals()` + `hashCode()` override хийх вэ?
3. `HashMap` ба `TreeMap` — ялгаа юу?
4. `Iterator.remove()` ба `list.remove()`-ийг loop дотор хийхэд ямар асуудал гарах вэ?
5. `List.of(...)` нь `ArrayList`-аас юугаараа ялгаатай вэ? (immutable)

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 1 — Two Sum](https://leetcode.com/problems/two-sum/) — HashMap сонгодог
- [LeetCode 49 — Group Anagrams](https://leetcode.com/problems/group-anagrams/) — `Map<String, List<String>>`

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `ConcurrentModificationException` | Loop дотор `.remove()` | `Iterator.remove()` эсвэл `removeIf` |
| `NullPointerException` `map.get(key)` | Key байхгүй | `getOrDefault(key, default)` |
| `HashSet` давхардал зөвшөөрнө | `equals/hashCode` override хийгээгүй | Хоёуланг нь override |
| `UnsupportedOperationException` `List.of(...).add(...)` | immutable list | `new ArrayList<>(List.of(...))` |
| `raw type` warning | `List list = new ArrayList()` | `List<String>` тодорхойлно |

---

**Дараагийн долоо хоног:** File I/O — [Week 14](../week-14-file-io/)
