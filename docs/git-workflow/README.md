# 🔀 Git Workflow — Lab-д зориулсан

← [Home](../home/) | [Repo](../../)

Lab 6-аас эхлэн бүх лаб GitHub дээр PR (Pull Request) хэлбэрээр өгнө. Энэ заавар нь **анх удаа** Git ашиглах оюутанд зориулагдсан.

---

## 📖 Нэр томъёо

| Үг | Утга |
|---|---|
| **Repo** | Repository-н товчлол. Код хадгалж байгаа папка + түүхтэй. |
| **Fork** | Repo-гийн хуулбарыг өөрийн GitHub account дээр үүсгэх |
| **Clone** | Repo-г компьютер дээрээ татан авах |
| **Commit** | Өөрчлөлтөө хадгалах (snapshot авах) |
| **Push** | Локал commit-уудаа GitHub руу илгээх |
| **Branch** | Үндсэн кодоос тусдаа "салбар" үүсгэж туршилт хийх |
| **Pull Request (PR)** | "Миний кодыг үндсэн repo руу нэмж өгөөч" гэсэн хүсэлт |
| **Merge** | PR-ийг зөвшөөрч үндсэн кодонд нэгтгэх |

---

## 🔄 Бүрэн Workflow (нэг зураг)

```
┌─────────────────────┐
│ UEFA-OPP/lab6-...   │  (багшийн repo)
│   main              │
└──────────┬──────────┘
           │ 1. Fork
           ▼
┌─────────────────────┐
│ <you>/lab6-...      │  (таны fork)
│   main              │
└──────────┬──────────┘
           │ 2. Clone
           ▼
┌─────────────────────┐
│ Локал компьютер     │
│   main              │
│   └─ exam/batbold   │  3. Branch үүсгэх
│         │           │  4. Код бичих
│         │           │  5. Commit
└─────────┬───────────┘
          │ 6. Push
          ▼
┌─────────────────────┐
│ <you>/lab6-...      │
│   exam/batbold      │
└──────────┬──────────┘
           │ 7. PR үүсгэх
           ▼
┌─────────────────────┐
│ UEFA-OPP/lab6-...   │
│   CI auto-grade     │  8. Автомат шалгалт
│   Merge (багш)      │  9. Merge
└─────────────────────┘
```

---

## Алхам 1: Fork хийх

1. Браузераар `https://github.com/UEFA-OPP/lab6-encapsulation` руу орно
2. Баруун дээд буланд **Fork** товч
3. Owner-д **өөрийнхөө account-ыг** сонгоно → **Create fork**
4. Одоо `https://github.com/<таны-username>/lab6-encapsulation` үүссэн

![Fork button location](https://docs.github.com/assets/cb-93774/images/help/repository/fork_button.png)

---

## Алхам 2: Clone хийх

Terminal нээгээд (Windows дээр Git Bash):
```bash
cd ~/Documents            # эсвэл ажиллах газраа сонгоно
git clone https://github.com/<таны-username>/lab6-encapsulation.git
cd lab6-encapsulation
```

> 💡 SSH key тохируулсан бол: `git clone git@github.com:<таны-username>/lab6-encapsulation.git`

---

## Алхам 3: Branch үүсгэх

```bash
git checkout -b exam/<өөрийн-нэр>
# Жишээ:
git checkout -b exam/batbold
```

**Яагаад branch?** `main`-д шууд бичвэл PR үүсэхгүй. Branch үүсгэхгүй бол шалгагдахгүй.

---

## Алхам 4: Кодоо бичих

IntelliJ-д `lab6-encapsulation` хавтсыг нээгээд (File → Open), `assignments/` дотор `.java` файлууд байна. `// TODO` коммент бүрийг өөрийн кодоор сольж бич.

---

## Алхам 5: Локал шалгах

```bash
bash scripts/run_tests.sh
```

- ✅ Ногоон = зөв
- ❌ Улаан = алдаа гарсан, уншиж, засна
- **Бүх тест ногоон болтол push хийх хэрэггүй** (CI quota хэмнэх)

---

## Алхам 6: Commit хийх

```bash
git status                                # ямар файл өөрчлөгдсөнийг харах
git add assignments/                       # зөвхөн assignments/ доторх файлыг stage хийнэ
git commit -m "feat: implement Character encapsulation"
```

**Commit мессежийн дүрэм:**
- `feat:` — шинэ feature
- `fix:` — алдаа засах
- `docs:` — тэмдэглэл (README)
- `refactor:` — логик өөрчлөхгүйгээр код сайжруулах

**❌ Муу commit мессеж:** `"update"`, `"aaa"`, `"fix"`
**✅ Сайн commit мессеж:** `"feat: add takeDamage validation for negative input"`

---

## Алхам 7: Push хийх

```bash
git push origin exam/<өөрийн-нэр>
```

Эхний удаа нууц үг эсвэл Personal Access Token асуух болно. SSH key тохируулсан бол шууд явна.

---

## Алхам 8: Pull Request үүсгэх

1. Браузераар fork repo-руу орно (`https://github.com/<you>/lab6-...`)
2. Шар өнгийн **"Compare & pull request"** товч гарна → дарна
3. Хэрэв харагдахгүй бол: **Pull requests** таб → **New pull request**
   - base: `UEFA-OPP/lab6-encapsulation` `main`
   - compare: `<you>/lab6-encapsulation` `exam/<өөрийн-нэр>`
4. **PR title:** `<Таны нэр> — <бүлэг>` (жишээ: `Батбольд — SE401`)
5. **Create pull request** дарна

---

## Алхам 9: CI автомат шалгалт

PR үүсгэсний дараа:
1. PR хуудасны доор **Checks** хэсэгт автоматаар шалгалт эхэлнэ (2–3 мин)
2. ⏳ Шар = running, ✅ Ногоон = pass, ❌ Улаан = fail
3. **Details** дарж алдаагаа харна
4. PR-ийн доод хэсэгт **оноогийн хүснэгт** автоматаар бичигдэнэ

---

## Алхам 10: Засвар хийх (олон удаа хийж болно)

Алдаатай бол:
```bash
# Локалд засаад
git add assignments/
git commit -m "fix: handle negative damage input"
git push
```

PR автоматаар шинэчлэгдэж, CI дахин ажиллана. **Deadline-ыг хүртэл хэдэн ч удаа push хийж болно** — сүүлийн push-ийн оноо тооцогдоно.

---

## 🆘 Түгээмэл асуудал

### `permission denied (publickey)`
SSH key тохируулаагүй эсвэл нэмж хадгалаагүй.
→ [Getting-Started §7](../getting-started/#7️⃣-ssh-key-сонголт-гэхдээ-санал-болгоно)

### `Updates were rejected because the remote contains work that you do not have locally`
Бусад хүн push хийсэн. Pull хийх хэрэгтэй:
```bash
git pull --rebase origin exam/<өөрийн-нэр>
git push
```

### Commit буруу файл нэмчихсэн
```bash
git reset HEAD~1 --soft      # сүүлийн commit-г буцаах, файлуудыг stage-д үлдээх
git restore --staged <буруу-файл>
git commit -m "..."
```

### PR-ээ хаах эсвэл засах
PR хуудас дээр **Edit** / **Close pull request** товч байна.

---

## 🎥 Санал болгох видео

- [Git in 100 seconds (Fireship)](https://www.youtube.com/watch?v=hwP7WQkmECE)
- [Fork + PR workflow (8 min)](https://www.youtube.com/watch?v=nT8KGYVurIU)
- [Монгол: Git-ийн үндэс](https://www.youtube.com/results?search_query=git+монгол+tutorial) — сонгож үзээрэй

---

## 📖 Интерактив дадлага

- **[learngitbranching.js.org](https://learngitbranching.js.org/)** — browser дотор branch, merge дасгал
- **[GitHub Skills](https://skills.github.com/)** — official интерактив курс
- **[Oh Shit, Git!](https://ohshitgit.com/)** — алдаа гаргасан бол яаж засах

---

**Дараагийн алхам:** [JUnit Basics](../junit-basics/) — тест яаж уншиж, ажиллуулах
