# ❓ FAQ — Байнга асуугддаг асуулт

← [Home](../home/) | [Repo](../../)

---

## 📚 Хичээлийн талаар

### Би AI ашиглаж болох уу?
Lab-уудад **ChatGPT/Copilot/Claude-ыг шууд код үүсгүүлэхэд** ашиглаж болохгүй. CI-д AI detector байгаа, өндөр score-той код manual review-д ордог. Гэхдээ:
- ✅ **Ойлгомжгүй ойлголтыг тайлбарлуулах** (жишээ нь "inheritance гэж юу вэ?")
- ✅ **Алдааны мессеж тайлбарлуулах**
- ✅ **Өөрийн бичсэн кодыг review хийлгэх** (commit хийхээс өмнө)
- ❌ **"Write me a Character class" гэх мэт асуулт** — энэ нь код хууларч байна

Prompt log хөтлөх (Lab 1-ийн дадал) хэвээр үлдэнэ.

### Deadline хэзээ вэ?
Lab repo-гийн README-д бичигдсэн. Ерөнхийдөө дараагийн лекц хүртэл (7 хоног).

### Хожимдсон бол?
Багштай холбоо барина. Харин репо дээр push хийсэн түүх хадгалагдах учраас "commit date"-ыг нэмэн шалгаж болно.

---

## 🛠️ Техникийн асуулт

### `git push` нууц үг асууж байна
2023 оны 8-р сараас GitHub нууц үг хүлээж авахаа болиулсан. Хоёр сонголт:

**A) SSH key** (санал болгоно):
[Getting-Started §7](../getting-started/#7️⃣-ssh-key-сонголт-гэхдээ-санал-болгоно)

**B) Personal Access Token (PAT):**
1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. **Generate new token** → `repo` scope сонго → Generate
3. Token-ыг хуулна (**зөвхөн 1 удаа харагдана!**)
4. `git push`-д нууц үгийн оронд PAT paste хийнэ

### `mvn: command not found` гарч байна
Бид Maven ашиглахгүй — энгийн `javac` + `scripts/run_tests.sh`. Error-г дахин шалгана уу.

### IntelliJ `No JDK selected` гарч байна
`File → Project Structure → Project → SDK → Add SDK → Download JDK` → Temurin 17 сонго.

### `.java` файл хар өнгөтэй болсон (red)
IntelliJ нь source root-ыг танихгүй байна.
`Right click on src folder → Mark Directory as → Sources Root`.

### `permission denied (publickey)` гарлаа
SSH key нэмэгдээгүй.
```bash
cat ~/.ssh/id_ed25519.pub   # хуулах
```
GitHub → Settings → SSH and GPG keys → New SSH key → paste.

### Commit хийсэн ч `git push` дээр юу ч илгээгдэхгүй байна
```bash
git status                    # юу staged байгааг хар
git log --oneline -5          # сүүлийн 5 commit
git push origin <branch-name> # branch нэрээ гарт бич
```

### Push хийсэн ч PR-т шинэчлэл гарахгүй байна
Fork repo-д push хийсэн эсэхийг шалга:
```bash
git remote -v
# origin  https://github.com/<taны-username>/lab6-...   (push)
```
Хэрэв `UEFA-OPP` гарч байвал буруу remote. Засах:
```bash
git remote set-url origin https://github.com/<таны-username>/lab6-encapsulation.git
```

### CI fail болсон, яаж лог харах вэ?
PR хуудас → Checks таб → ❌ тэмдэгтэй step дарна → лог гарна. **Үндсэн алдааг дээрээс доошоо унших**.

---

## 🧪 Тестийн талаар

### Локал дээр тест яаж ажиллуулах вэ?
```bash
bash scripts/run_tests.sh
```
[JUnit Basics](../junit-basics/)-аас дэлгэрэнгүй.

### Зарим тест нь pass болж, зарим нь fail байна
Энэ нь **хэвийн** — Core/Stretch/Bonus-ийн аль нэгэнд хүрэх хэмжээний код бичсэн байна. Оноо пропорциональ тооцогдоно.

### Тест файлыг өөрчилж болох уу?
**❌ Үгүй.** `tests/` хавтас read-only. Өөрчилбөл PR автоматаар татгалзана.

### AI detector яагаад миний дээр HIGH score өгсөн бэ?
Нийтлэг шалтгаанууд:
- Хэт их Javadoc коммент (`/** @param ... */`)
- AI-нд түгээмэл phrase ("This method calculates the ...")
- Ашиглагдаагүй import олон
- Мөрүүд нь хэт жигд урт

→ Кодоо илүү **"хүн шиг"** бич: энгийн single-line коммент, өөрийн хэлээр (МН), ашиглаагүй import устгах.

---

## 💡 Хичээлийн агуулгын талаар

### `private` яагаад хэрэгтэй вэ? `public` үргэлж хийж болох биз дээ?
Технически болно. Гэхдээ хэн нэгэн (өөрөө ч бай) `hero.hp = -9999` гэж бичээд системийг "эвдчихдэг". Encapsulation энийг **зориудаар боломжгүй** болгодог. 20-30 мөрийн код дээр яг одоохондоо асуудалгүй ч 10,000 мөрт код дээр маш чухал.

### `extends` ашиглах уу `interface` ашиглах уу?
- **`extends`** (inheritance) — "is a" (Dog is an Animal)
- **`interface`** — "can do" (Bird can fly, Airplane can fly — ижил зан үйл, өөр онцлог)
- Java зөвхөн нэг class-ээс `extends` хийнэ, гэхдээ **олон interface** implement хийж болно
- Эргэлзвэл interface-ээс эхэл — илүү уян хатан

### `static` method хэзээ ашиглах вэ?
Обьекттой холбоогүй, зөвхөн тохиргоо эсвэл туслах function-д. Жишээ:
- `Math.max(a, b)` — ямар ч Math object үгүй
- `Character.createWarrior(name)` — factory method
- Хэрэв method дотор `this` ашиглаагүй бол `static` болгож болно

---

## 🆘 Надад **одоо** тусламж хэрэгтэй

1. [Debugging Tips](../debugging/) шалгасан уу?
2. Алдааны мессежээ 5 удаа уншсан уу?
3. Google хайсан уу? (Stack Overflow маш хүчтэй)
4. ChatGPT-с **ойлголт** асуусан уу? (код биш, ойлголт)
5. Bөгөд найздаа тайлбарласан уу? (rubber duck)

Бүгдийг нь туршсан бол — **GitHub Discussions** таб дээр асуу:
- Кодоо хавсаргах (зөвхөн тэр хэсэг)
- Алдаа мессежээ бүрэн хавсаргах
- "Юу хүлээж байсан vs юу болсон" хоёрыг бич
- Ямар туршилт хийж үзсэнээ жагсаа

---

## 🙋 Асуулт нь эндээс олдохгүй бол

[Issue нээ](../../../issues/new) — энэ FAQ-д нэмэгдэх болно.
