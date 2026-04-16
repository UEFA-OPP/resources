# Week 14 — File I/O

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab14-file-io](../../../../lab14-file-io)

**Нэг өгүүлбэрээр:** File I/O бол програмаас файл руу бичих, уншихад хэрэглэгддэг Java API — `FileReader/Writer`, `BufferedReader`, `try-with-resources`.

---

## 🎯 Энэ долоо хоногт сурах

1. `FileReader` / `FileWriter` — character stream үндэс
2. `BufferedReader` / `BufferedWriter` — мөрөөр нь унших/бичих
3. `try-with-resources` — resource автомат хаах
4. `Path`, `Files.readString`, `Files.writeString` (modern API)

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java File Reader / Writer](https://www.youtube.com/watch?v=ScUJx4aWRi0) | 10 мин | 🟢 Эхлэгч |
| [Coding with John — try-with-resources](https://www.youtube.com/watch?v=9Q1Y5fLrXT8) | 9 мин | 🟡 Дунд |
| [Telusko — File Handling in Java](https://www.youtube.com/watch?v=BIAv1-MLFBg) | 12 мин | 🟢 Эхлэгч |
| [Amigoscode — Reading & Writing Files](https://www.youtube.com/@amigoscode/search?query=file+io) | 14 мин | 🟡 Дунд |

**Хамгийн бага:** эхний 2 видеоны аль нэгийг үз.

---

## 📖 Унших

- [Oracle — File I/O (NIO.2)](https://docs.oracle.com/javase/tutorial/essential/io/fileio.html) — албан ёсны
- [Baeldung — Reading a File in Java](https://www.baeldung.com/reading-file-in-java) — олон арга
- [GeeksForGeeks — File Handling](https://www.geeksforgeeks.org/file-handling-in-java/) — жишээтэй
- [Refactoring.Guru — Extract Class](https://refactoring.guru/extract-class) — **Монгол орчуулгатай**

---

## 🎮 Интерактив дадлага

- [HackerRank — Java Output Formatting](https://www.hackerrank.com/challenges/java-output-formatting/problem) + файл гаргалт
- [Exercism — File Sniffer (Java)](https://exercism.org/tracks/java/exercises) — File хайлт
- [HyperSkill — Files and Streams topic](https://hyperskill.org/learn/topic/2124)

---

## 💡 Code жишээ

**❌ Муу (resource хаагдаагүй, `try/finally` гараар):**
```java
public void saveGame(Player p) {
    FileWriter w = null;
    try {
        w = new FileWriter("save.txt");
        w.write(p.getName() + "\n");
        w.write(p.getHp() + "\n");
    } catch (IOException e) {
        e.printStackTrace();
    } finally {
        try {
            if (w != null) w.close();  // хэн мартвал leak
        } catch (IOException e) { }
    }
}
```

**✅ Сайн (`try-with-resources` + `BufferedReader`):**
```java
import java.io.*;
import java.nio.file.*;
import java.util.*;

public class SaveSystem {

    public void saveGame(Player p) throws IOException {
        try (BufferedWriter w = Files.newBufferedWriter(Path.of("save.txt"))) {
            w.write(p.getName());
            w.newLine();
            w.write(String.valueOf(p.getHp()));
            w.newLine();
            w.write(String.valueOf(p.getGold()));
        }
        // w автоматаар хаагдана — амжилт эсвэл exception аль алинд
    }

    public Player loadGame() throws IOException {
        try (BufferedReader r = Files.newBufferedReader(Path.of("save.txt"))) {
            String name = r.readLine();
            int hp = Integer.parseInt(r.readLine());
            int gold = Integer.parseInt(r.readLine());
            return new Player(name, hp, gold);
        }
    }

    // Бүх мөрийг нэг мөрөнд унших (жижиг файлд)
    public String loadRaw() throws IOException {
        return Files.readString(Path.of("save.txt"));
    }
}
```

Ялгаа:
- `try-with-resources` нь `close()` автомат дуудна
- `BufferedReader` нь мөрөөр унших, хурдан
- `Files.readString` нь нэг мөрөнд бүх файл уншина
- Exception зөв propagate болно

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `FileReader` ба `BufferedReader` — ялгаа юу? Яагаад buffered нь хурдан вэ?
2. `try-with-resources` ажиллахын тулд class ямар interface implement хийсэн байх ёстой вэ? (`AutoCloseable`)
3. Character stream (`Reader`) ба byte stream (`InputStream`) — хэзээ аль нь вэ?
4. `Files.readAllLines` vs `Files.lines` — ялгаа? (memory)
5. `FileNotFoundException` ба `IOException` — харилцан хэрхэн хамаарах вэ?

---

## 🏆 Challenge (Lab-с гадуур)

- [LeetCode 192 — Word Frequency (Shell)](https://leetcode.com/problems/word-frequency/) — Java-аар хийвэл file read + Map
- HackerRank — "Java BufferedReader"

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `FileNotFoundException` | Файл байхгүй эсвэл зам буруу | Absolute path эсвэл `Files.exists(...)` шалгах |
| Resource leak warning | `close()` дуудаагүй | `try-with-resources` ашиглах |
| `NumberFormatException` | `parseInt` null/string дээр | `readLine()` null шалгах |
| Файл хоосон бичсэн | `flush()` хийгээгүй / `close` алгассан | `try-with-resources`-ээр найдвартай |
| Кирилл үсэг эвдэрсэн | Default charset буруу | `StandardCharsets.UTF_8` заах |

---

**Хичээл дууслаа!** 🎉 Эцсийн төслөө [home](../home/) хуудаснаас үзээрэй.
