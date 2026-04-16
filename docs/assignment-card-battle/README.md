# 🎴 Card Battle Game — Бие даалт

← [Home](../home/) | [Repo](../../) | 🟣 Assignment: [assignment-card-battle](../../../../assignment-card-battle)

**Нэг өгүүлбэрээр:** Энэ бие даалт бол таны OOP-ийн эзэмшилтийг **нэг тоглоомоор** нотлох үйл явц — 3-4 долоо хоногийн туршид class, inheritance, polymorphism, abstraction, exception, collection, file I/O бүгдийг нэгтгэж, **UI/UX** мэргэжлийнхээ өнгийг дээр нь нэмнэ.

---

## 🎯 Юу сурах вэ?

1. **OOP-ийг хамтад** — Week 6-14-д сурсан бүх ойлголт нэг кодбааз дээр ажиллана
2. **UI/UX deliverable** — wireframe, persona, UX writing, ASCII гоёл — зөвхөн код биш
3. **3-4 долоо хоногийн project flow** — жижиг задрал, долоо хоног бүр commit, iteration
4. **Dev-log бичиг** — өөрийн үгээр юу сурсан, юу бэрхшээл тулгарсан тухай reflection
5. **AI policy-тэй ажиллах** — AI-г **зөвөөр** ашиглах, хэзээ хэрэглэж болохгүйг мэдэх
6. **User testing** — 3 бодит хүнд тоглуулж, ажиглалтаа бичгээр гаргах

---

## 📐 Архитектурын хандлага

Auto-grader нь тодорхой class-уудын нэрийг шалгадаг: `Card`, `AttackCard`, `HealCard`, `BuffCard`, `Player`, `Deck`, `Rarity`. Дараах бүтэц санал болгож байна:

```
src/
├── cards/       — Card (abstract), AttackCard, HealCard, BuffCard, CreatureCard, Rarity (enum)
├── players/     — Player (abstract), HumanPlayer, AIPlayer
├── game/        — Game, Deck, Turn, Battlefield
└── io/          — ConsoleRenderer, GameSaver, InputReader
```

**Яагаад энэ бүтэц?**
- `cards/` — бүх карт төрөл нэг `abstract class Card`-аас `extends` хийнэ → polymorphism
- `players/` — `Human` ба `AI` нэг адил `Player.takeTurn()` method-г өөр өөрөөр хэрэгжүүлнэ
- `game/` — тоглоомын flow (turn loop, deck shuffle) — UI-аас тусгаарлагдсан
- `io/` — input/output, save/load — энэ давхаргыг солих нь тоглоомын логикэд нөлөөлөхгүй (Week 11 abstraction)

---

## 🎨 UI/UX материал

Таны давуу тал — UI/UX мэргэжил. Энэ хэсэгт хамгийн их цаг зарцуулаарай.

**Figma & wireframing:**
- [Figma Learn](https://help.figma.com/hc/en-us/categories/360002051613-Learn-Design) — албан ёсны tutorial
- [Figma YouTube channel](https://www.youtube.com/@Figma) — "Figma for beginners" цуврал
- [Excalidraw](https://excalidraw.com/) — хурдан wireframe-д зориулсан үнэгүй хэрэгсэл
- [Balsamiq Wireframing Academy](https://balsamiq.com/learn/) — low-fidelity зарчмууд

**Persona & UX writing:**
- [Xtensio — Persona templates](https://xtensio.com/user-persona-template/) — үнэгүй загвар
- [HubSpot Persona Generator](https://www.hubspot.com/make-my-persona) — мастер хийх эхлэл
- [NN/g — UX Writing articles](https://www.nngroup.com/topic/writing-web/) — мэргэжлийн зөвлөмжүүд
- [Microsoft Writing Style Guide](https://learn.microsoft.com/en-us/style-guide/welcome/) — tone/voice дээд стандарт

**ASCII art & ANSI color:**
- [patorjk.com/software/taag](https://patorjk.com/software/taag/) — ASCII title generator
- [asciiart.eu](https://www.asciiart.eu/) — бэлэн зурагны сан
- [ANSI color codes](https://en.wikipedia.org/wiki/ANSI_escape_code#Colors) — консол дээрх өнгөт текст
- [Bash/Java ANSI cheatsheet](https://gist.github.com/RabaDabaDoba/145049536f815903c79944599c6f952a) — code-т хуулах

---

## 🃏 Тоглоомын дизайн судлах

Өөрийн тоглоомоо хийхээсээ өмнө мастеруудыг ажиглаж сур:

- **[Hearthstone](https://hearthstone.blizzard.com/)** — картны визуал дизайн, mana crystal, hero power
- **[Slay the Spire](https://www.megacrit.com/)** — deckbuilding механик, turn loop хэрхэн уялддаг
- **[Balatro](https://www.playbalatro.com/)** — орчин үеийн indie, энгийн UI-гаар гүнзгий механик
- **[Pokemon TCG Live](https://tcg.pokemon.com/)** — эхлэгчдэд ээлтэй, type-strength харьцаа ойлгомжтой

> 💡 Санаа хулгайлж болно — **UX-ийн хариуцлагыг өөрөө үүр**. Эдгээр тоглоомуудын юу нь сайхан, юу нь эвгүй вэ гэдгийг `docs/ux-audit/README.md`-д өөрийн үгээр тэмдэглээрэй.

---

## 📺 Видео — тоглоом хийхийн тулд

| Видео | Хугацаа | Түвшин |
|---|---|---|
| [Coding with John — Console Game in Java](https://www.youtube.com/@CodingWithJohn/search?query=console+game) | 25 мин | 🟡 Дунд |
| [Bro Code — Java OOP game project](https://www.youtube.com/@BroCodez/search?query=java+game) | 40 мин | 🟡 Дунд |
| [Amigoscode — Building a Java project](https://www.youtube.com/@amigoscode/search?query=java+project) | 30 мин | 🟡 Дунд |
| [Fireship — Clean Code principles](https://www.youtube.com/@Fireship/search?query=clean+code) | 6 мин | 🟢 Эхлэгч |

---

## 🧪 User testing guide

**3 хүнтэй user test хэрхэн явуулах вэ?**

1. **Сонгох:** 3 өөр арын хүмүүс — 1 нь программист, 2 нь тоглоом тоглодоггүй хүн байхад тохиромжтой
2. **Бэлтгэх:** тоглоомоо цэвэр `.jar` болгож, `README.md`-д 3 мөрөөр хэрхэн ажиллуулахыг заа
3. **Ажиглах:** тэднийг тайвшруулж суулгаад, **юу хийхийг заахгүй** — зүгээр "тогло" гээд харж байгаарай
4. **Бичих:** дараах 4 зүйлийг тэмдэглэ (нэг хүн тутамд):
   - Юу дээр **гацсан** бэ?
   - Юуг ойлгоогүй вэ?
   - Юу **инээмсэглэсэн** бэ? (positive moment)
   - Юуг өөр хэрэглэсэн бэ (та төсөөлсөнөөс)?
5. **Дүгнэх:** `docs/user-test-report/README.md`-д findings + **3 сайжруулалт** бичнэ

---

## 💡 Жишээ код: 1 карт хэрхэн хийх

```java
public class AttackCard extends Card {
    private final int damage;

    public AttackCard(String name, int manaCost, int damage, Rarity rarity) {
        super(name, manaCost, rarity);
        if (damage < 0) {
            throw new IllegalArgumentException("Damage cannot be negative");
        }
        this.damage = damage;
    }

    @Override
    public void play(Player caster, Player target) {
        target.takeDamage(damage);
        System.out.println(caster.getName() + " cast " + getName()
            + " — " + damage + " damage!");
    }
}
```

Тайлбар:
- `extends Card` — inheritance (Week 9)
- `@Override play()` — polymorphism (Week 10), карт бүр өөр өөрөөр тоглогдоно
- `private final int damage` — encapsulation (Week 6) + immutability
- `throw new IllegalArgumentException` — exception handling (Week 12)

---

## 🏆 Inspiration — өмнөх оюутны жишээ

> 🎓 **First cohort — be the example!**
>
> Энэ хичээлийн **анхны** оюутан болсон та өмнө жишээгүй. Таны submission нь дараагийн оюутнуудад **inspiration** болох болно. Санал болгож буй level — Balatro-ийн минимализм, Hearthstone-ийн flavor, Slay the Spire-ийн deck логик.

---

## ⚠️ AI хэрэглэх policy

| Зөвшөөрөгдсөн | Хориотой |
|---------------|----------|
| ✅ Концепци асуух ("polymorphism гэж юу вэ?") | ❌ Код бичүүлэх ("`Fireball` class-ыг бичиж өг") |
| ✅ Error message орчуулуулах | ❌ Бүхэл файлыг хуулж тавих |
| ✅ Wireframe-н санаанд reference хайх | ❌ UX writing-ыг AI-гаар орлуулах |
| ✅ Dev-log-ийн хэлний алдаа засуулах | ❌ Dev-log-ийг AI-аар бүтэн бичүүлэх |

- **AI detector** auto-grader-т ажиллана. `HIGH` түвшинд **50% хасагдана**.
- `dev-log/README.md`-г **өөрийн үгээр** бич — энэ таны кодын стилийг баталгаажуулна.

---

**Буцах:** [Home](../home/) | **Эхлэх:** Lab-аас Week 1-ээр эхлэх — [Week 1](../week-01-intro/)
