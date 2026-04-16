# Week 4 — Array & Loop

← [Home](../home/) | [Repo](../../) | 🟢 Lab: [lab4-arrays](../../../../lab4-arrays)

**Нэг өгүүлбэрээр:** Array гэдэг нь олон утгыг **нэг хувьсагчид** дараалалтай хадгалах сав — loop-тэй хамтарснаар олон зууны ширхэг өгөгдөл дээр нэг логикоор ажиллах боломжтой болно.

---

## 🎯 Энэ долоо хоногт сурах

1. Array зарлах, үүсгэх, утга оруулах (`int[] nums = new int[5]`)
2. Index-ээр хандах (0-ээс эхлэдэг), `.length` property
3. `for` loop, for-each loop-оор array-г дамжин өнгөрөх
4. Max, min, sum, average — array дээр ажиллах үндсэн алгоритмууд

---

## 📺 Видео (эхлээд үзээрэй)

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Bro Code — Java arrays](https://www.youtube.com/watch?v=yRA5fM4fJUA) | 12 мин | 🟢 Эхлэгч |
| [Coding with John — Arrays in Java](https://www.youtube.com/@CodingWithJohn/search?query=arrays) | 13 мин | 🟢 Эхлэгч |
| [Telusko — Arrays in Java](https://www.youtube.com/@Telusko/search?query=java+array) | 11 мин | 🟢 Эхлэгч |
| [Neso Academy — For-each loop](https://www.youtube.com/@nesoacademy/search?query=for+each+java) | 7 мин | 🟡 Дунд |

**Хамгийн бага:** Bro Code-ийн array видеог бүтнээр үз.

---

## 📖 Унших

- [Oracle — Arrays](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/arrays.html) — албан ёсны
- [W3Schools — Java Arrays](https://www.w3schools.com/java/java_arrays.asp) — алхамчилсан
- [Baeldung — Java Arrays Guide](https://www.baeldung.com/java-arrays-guide) — бүрэн
- [GeeksForGeeks — Arrays in Java](https://www.geeksforgeeks.org/arrays-in-java/) — олон жишээ

---

## 🎮 Интерактив дадлага

- [HackerRank — Java 1D Array](https://www.hackerrank.com/challenges/java-1d-array-introduction/problem) — анхны дасгал
- [HackerRank — Array Reversal](https://www.hackerrank.com/challenges/java-1d-array/problem) — урвуулах
- [Exercism — High Scores (Java)](https://exercism.org/tracks/java/exercises/high-scores) — max, top-3 олох

---

## 💡 Code жишээ

**Оноо дээр max, min, average олох:**
```java
public class ScoreStats {
    public static void main(String[] args) {
        int[] scores = {87, 92, 65, 78, 95, 80, 72};

        int max = scores[0];
        int min = scores[0];
        int sum = 0;

        for (int score : scores) {
            if (score > max) max = score;
            if (score < min) min = score;
            sum += score;
        }

        double avg = (double) sum / scores.length;

        System.out.println("Max: " + max);
        System.out.println("Min: " + min);
        System.out.println("Average: " + avg);
    }
}
```

Тайлбар:
- Max/min-ийг **эхний** элементээр эхлүүлэх ёстой (0-ээс биш)
- `for-each` нь индекс хэрэггүй үед илүү цэвэрхэн
- `(double) sum` — int-ээс double руу хөрвүүлж, average-г 0 гэж буухаас сэргийлнэ
- `scores.length` нь array-н хэмжээ — method биш property (`.length()` биш)

---

## 🔑 Түлхүүр асуултууд (өөрийгөө шалгах)

1. `scores.length` ба `scores[length]`-ийн ялгаа? Яагаад `scores[scores.length]` нь error болох вэ?
2. `int[] a = {1,2,3}` ба `int[] a = new int[3]`-ийн ялгаа?
3. For-each loop-оор array-ийн элементийг өөрчилж чадах уу?
4. `ArrayIndexOutOfBoundsException` хэзээ гарах вэ? Яаж урьдчилан сэргийлэх вэ?
5. `int[]` ба `String[]`-ийн зарлалт, анхдагч утга (default) юу байх вэ?

---

## 🏆 Challenge

- HackerRank — "Java 2D Array" — матриц (Week 4-гийн stretch)
- Array-г урвуу талд нь (reverse) байрлуулах — шинэ array үүсгэхгүйгээр

---

## 🐛 Нийтлэг алдаа

| Алдаа | Шалтгаан | Шийдэл |
|---|---|---|
| `ArrayIndexOutOfBoundsException: 5` | Length-с гадуур index-д хандсан | `i < arr.length` шалгуур зөв бай |
| `NullPointerException` — array-д | `new int[]` хийгээгүй, зөвхөн зарласан | `new int[n]` эсвэл `{...}` initializer |
| `length()` vs `length` | String-д `length()`, array-д `length` | Array-д хаалтгүй: `arr.length` |
| Max-ийг 0-оор эхлүүлсэн, бүх утга сөрөг байхад үр дүн буруу | Initial value буруу | `arr[0]`-оор эхлүүл |
| For-each-д индекс хэрэгтэй мөртлөө хэрэглэсэн | For-each-д i байхгүй | Энгийн `for (int i = 0; ...)` ашигла |

---

**Дараагийн долоо хоног:** Class & Object — [Week 5](../week-05-class-object/)
