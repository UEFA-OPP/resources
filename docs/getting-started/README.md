# 🚀 Getting Started

← [Home](../home/) | [Repo](../../)

Анх удаа Java, IntelliJ, Git-тэй ажиллаж байгаа оюутанд зориулсан setup.

---

## ✅ Шалгах жагсаалт

Хичээл эхлэхээс өмнө:
- [ ] **Java JDK 17+** суусан ба `java -version` ажиллаж байна
- [ ] **IntelliJ IDEA Community** суусан (үнэгүй)
- [ ] **Git** суусан ба `git --version` ажиллаж байна
- [ ] **GitHub account** үүсгэсэн
- [ ] **GitHub username** багшид мэдэгдсэн
- [ ] Анхны Java project үүсгэж `Hello World` ажиллуулсан

---

## 1️⃣ Java JDK суулгах

### macOS
```bash
# Homebrew-тэй бол
brew install openjdk@17

# Эсвэл албан ёсны installer
# https://adoptium.net/temurin/releases/?version=17
```

### Windows
1. [Adoptium Temurin 17](https://adoptium.net/temurin/releases/?version=17) — `.msi` installer татах
2. Next → Next → Install
3. Шинэ terminal нээгээд `java -version` шалгах

### Linux (Ubuntu)
```bash
sudo apt update
sudo apt install openjdk-17-jdk
java -version
```

**Амжилттай суулгасны баталгаа:**
```
openjdk version "17.0.x" ...
```

---

## 2️⃣ IntelliJ IDEA Community суулгах

- [jetbrains.com/idea/download](https://www.jetbrains.com/idea/download/) → **Community Edition** татна
- Ultimate биш, Community хангалттай (үнэгүй)
- Суулгасны дараа анх нээхэд "Import settings" → **Do not import**

**Видео заавар:** [IntelliJ IDEA setup for beginners (5 мин)](https://www.youtube.com/watch?v=K5YMgoYp7jI)

---

## 3️⃣ Анхны Java Project

1. IntelliJ нээгээд **New Project**
2. Тохиргоо:
   - Name: `HelloWorld`
   - Language: **Java**
   - Build system: **IntelliJ** (Maven биш)
   - JDK: таны суулгасан 17-р хувилбар
3. `src/` дотор `Main.java` үүснэ
4. Дараах кодыг бич:
   ```java
   public class Main {
       public static void main(String[] args) {
           System.out.println("Сайн байна уу, OOP!");
       }
   }
   ```
5. `main`-ын хажууд ногоон ▶ товч дарж ажиллуулна
6. Дэлгэц дээр "Сайн байна уу, OOP!" гарна

---

## 4️⃣ Git суулгах

### macOS
```bash
# Apple Developer Tools дотор байгаа
xcode-select --install
# эсвэл
brew install git
```

### Windows
[git-scm.com/download/win](https://git-scm.com/download/win) — default settings-ээр install хийнэ.
Git Bash гэдэг terminal-ыг хамт суулгана — Windows дээр Git ашиглахад энийг хэрэглэнэ.

### Linux
```bash
sudo apt install git
```

---

## 5️⃣ Git-ийг анх удаа тохируулах

```bash
git config --global user.name "Батаа Баярсайхан"
git config --global user.email "your-email@example.com"
# GitHub-д бүртгүүлсэн имэйлийг ашиглана
```

---

## 6️⃣ GitHub account үүсгэх

1. [github.com/signup](https://github.com/signup)
2. **Username-г careful сонгоно** — CV-д харагдана
3. Имэйл баталгаажуулна
4. 2FA асаах нь ЗҮЙТЭЙ (settings → security)
5. Багшид username-ээ мэдэгд — Classroom-д урих

---

## 7️⃣ SSH key (сонголт, гэхдээ санал болгоно)

Нууц үг бүр удаа асуухгүй болгоно:
```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
# Enter 3 удаа дарна (default path, no passphrase)

cat ~/.ssh/id_ed25519.pub
# Гарсан зүйлийг хуулна
```

GitHub → Settings → SSH keys → **New SSH key** → paste хийж хадгална.

Шалгах:
```bash
ssh -T git@github.com
# "Hi <username>! You've successfully authenticated..."
```

---

## 🎥 Санал болгох видео

- [Bro Code — Setting up Java (10 min)](https://www.youtube.com/watch?v=Z1Yd7upQsXY)
- [Derek Banas — Intro to Java (30 min)](https://www.youtube.com/watch?v=WPvGqX-TXP0)
- [Git in 15 minutes](https://www.youtube.com/watch?v=USjZcfj8yxE)

---

## 🐛 Нийтлэг асуудал

| Асуудал | Шийдэл |
|---|---|
| `java: command not found` | PATH-д JDK нэмнэ. macOS дээр `export PATH="$PATH:$(/usr/libexec/java_home -v 17)/bin"` |
| IntelliJ "No JDK selected" | File → Project Structure → SDK → + → Download JDK |
| `git push` нууц үг асууна | [SSH key тохируул](#7️⃣-ssh-key-сонголт-гэхдээ-санал-болгоно) эсвэл [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) ашигла |

---

**Дараагийн алхам:** [Git Workflow](../git-workflow/) — Lab repo-г fork хийж, PR үүсгэж сурах
