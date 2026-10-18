# 🎬 Claude هو اللي منتج الريل ده — ازاي تخلي Claude Code المونتير بتاعك

المونتاج بياكل وقتك: قص، captions، زوم، ألوان، graphics ومزيكا… وكل ريل بياخد ساعات.
الريل اللي شفته على Instagram اتمنتج كله بـ **Claude Code**: أنا بكتب وبصوّر، وهو بيعمل الباقي بالـ code.

هنا هتلاقي **الطريقة نفسها خطوة بخطوة**: الـ 4 خطوات اللي قلتها في الريل، الـ pipeline شغال ازاي، الـ Prompts اللي تبدأ بيها، وأهم الدروس اللي اتعلمناها بالطريقة الصعبة.

> 💡 انسخ الـ Prompts زي ما هي، وغيّر بس الحاجات اللي بين `[ ]`.

> ⚠️ **مش هتلاقي هنا الـ skill أو الـ templates بتاعتي** — دي معمولة على الـ style بتاعي. وانت هتطلع أحسن لما تبني بتوعك، لأن نسخة من style حد تاني بتبان إنها نسخة.

---

## 📦 هتطلع بإيه في الآخر؟

من فيديو خام واحد (مثلاً 3–4 دقايق متصوّر بالموبايل)، ريل جاهز **1080×1920** فيه:

- ✂️ **القص**: السكوت، التهتهة، الإعادات، وكل لحظة بتبص فيها على الـ script.
- 💬 **Captions**: كلمة كلمة، بالمصري، والكلام الإنجليزي يفضل مكتوب إنجليزي.
- 🔍 **Zoom**: punch-in على أهم الجمل.
- 🎨 **الألوان**: grade ثابت متظبط على ريل reference انت بتحبه.
- ✨ **Motion graphics**: معمولة بالـ code (React / Remotion)، وكل واحدة بتظهر على الكلمة اللي بتقولها بالظبط.
- 🪝 **Hook + End card**: hook متحرك في أول 3 ثواني، و CTA بكلمة الكومنت.
- 🎵 **مزيكا و sound design**: مزيكا في الخلفية، whooshes و pops.
- 📝 **Caption و hashtags** للبوست جاهزين.

---

## 🔌 الأول: محتاج إيه؟

| الأداة | بتعمل إيه |
|---|---|
| **Claude Code** | الـ agent اللي بيكتب ويشغّل كل حاجة |
| **Python 3.10+** | الـ transcription، الـ face tracking، و script الـ render |
| **ffmpeg** | القص، الألوان، تركيب الطبقات، والـ export |
| **faster-whisper** | transcription بتوقيت كل كلمة (الـ GPU بيسرّع، بس الـ CPU شغال) |
| **MediaPipe** | بيتتبع وشك، عشان يعرف امتى بتبص بعيد عن الكاميرا |
| **Node 20+ و Remotion** | الـ motion graphics مكتوبة كـ React components |
| **الـ References بتاعتك** | 3–5 ريلز ألوانهم والـ captions والـ graphics بتاعتهم عاجبينك |

مش محتاج تعرف تكتب code. محتاج تعرف **انت عايز إيه**، وتعرف تقول "لأ، مش كده" لحد ما يطلع صح.

لو لسه مسطّبتش Claude Code، الشرح الرسمي هنا: https://docs.claude.com/en/docs/claude-code/overview

---

## 🪜 الـ 4 خطوات (زي ما قلتهم في الريل)

### 1️⃣ افتح Claude Code و"عيّنه" عندك

اعمل folder جديد، افتح فيه Claude Code، وقوله بكلام عادي:

- **انت مين**: الـ niche بتاعك، الجمهور، اللغة واللهجة.
- **بتعمل إيه**: ريلز vertical، talking-head… إلخ.
- **شغلته إيه**: "من النهارده انت المونتير بتاعي".

واطلب منه يجهّز المشروع: يسطّب الأدوات، يعمل folder اسمه `inbox/` للفيديوهات الخام، و `out/` للريلز الجاهزة، وملف rules يقراه كل session.

### 2️⃣ اديله References

هنا الـ style بتاعك بيتولد. اديله:

- **الألوان**: screenshot أو ريل ألوانه عاجباك. اطلب منه **يقيس** الحيطة والجلد والـ shadows في الـ reference، ويظبط الفيديو بتاعك على نفس الأرقام.
- **الـ Captions**: ريل شكل الـ captions فيه عاجبك (الخط، اللون، الحجم، المكان، كلمة كلمة ولا جملة كاملة).
- **الـ Graphics**: 2–4 ريلز الـ motion graphics فيهم عاجباك. اطلب منه يوصف **القواعد** اللي ورا الشكل ده (المسافات، لون accent واحد، العناصر بتدخل ازاي، كل واحدة بتفضل قد إيه) ويكتبها كـ design system.
- **ريلزك القديمة**: عشان يعرف انت عملت إيه قبل كده.

### 3️⃣ قسّموا الشغل

| انت | Claude |
|---|---|
| بتكتب الـ script | بيعمل transcribe لكل كلمة بالتوقيت |
| بتصوّر | بيتتبع وشك ويقص كل بصّة على الـ script |
| بتقرر الريل يقول إيه | بيكتب الـ captions بالمصري |
| بتوافق | بيعمل الـ graphics بالـ code، والألوان، والمكس، والـ export |

**القرار بتاع الريل هيقول إيه بيفضل بتاعك انت.** Claude بيقترح القص، وانت اللي بتوافق.

### 4️⃣ عدّل لحد ما يبقى perfect… وبعدين احفظه

أول ريل مش هيبقى perfect. احنا أخدنا حوالي **4 ريلز** feedback، حاجات زي:
*"نزّل الـ captions شوية"*، *"الألوان أبرد"*، *"متقصش كلامي"*، *"الـ graphic مش ماشي مع اللي بقوله"*.

**السر:** كل مرة تصحح حاجة، اطلب منه **يكتب التصحيح ده في ملف الـ rules** (وفي الـ code لو ينفع) عشان ميكررش نفس الغلطة تاني. ولما النتيجة تبقى زي ما انت عايز، قوله:

> "احفظ كل حاجة اتفقنا عليها كـ skill."

ومن ساعتها، أي فيديو جديد بيطلع بالـ style بتاعك من أول مرة.

---

## ⚙️ الـ Pipeline شغال ازاي؟

```
raw clip ──► 1. transcribe ──► 2. face tracking ──► 3. edit decision ──► 4. graphics
                (words +          (when do you          (which sentences,      (React/Remotion,
                 timestamps)       look down?)           captions, zooms)       one per phrase)
                                                                                     │
finished reel ◄── 7. checks ◄── 6. export ◄── 5. render: cut + grade + captions + composite + music
```

1. **Transcribe**: Whisper بتوقيت كل كلمة. كل الخطوات اللي بعد كده شغالة على **الكلمات** مش على الثواني.
2. **Face tracking**: نقط الوش في كل frame؛ ميلة الراس بتقولك امتى انت بتقرا. اقطع الحتت دي، بس **الأجزاء الساكتة بس**: عمره ما يقص كلمة انت بتقولها.
3. **Edit decision**: ملف JSON صغير لكل ريل: الجمل اللي هتفضل، الكلمات اللي تتشال، تصحيحات اللهجة في الـ captions، الـ zooms، الـ hook، كلمة الكومنت، ولستة الـ graphics.
4. **Graphics**: كل graphic عبارة عن React component بيتعمل render لفيديو شفاف، و**متربط بالكلمات** اللي بيشرحها (يبدأ على كلمة A ويخلص على كلمة B)، مش بتوقيت ثابت.
5. **Render**: ffmpeg بيقص الكلمات اللي هتفضل، يحط الألوان، يحرق الـ captions، يركّب الـ graphics، يضيف المزيكا والـ sound effects، ويظبط الصوت.
6. **Export**: H.264، 1080×1920، square pixels، ألوان bt709، و faststart.
7. **Checks**: طلّع frame من نص كل graphic و**بص عليه بعينك**.

خلّي كل حاجة في **ملف واحد قابل للتعديل لكل ريل** (الـ edit decision). كده تعديل الريل معناه تغيّر كام سطر، مش تعيد مونتاج timeline من الأول.

---

## 💬 الـ Prompts اللي تبدأ بيها

انسخ، عدّل، والصق في Claude Code. وكل ما تكتبهم بكلامك انت أحسن؛ دول نقطة بداية بس.

### 🛠️ 1. التجهيز (أول Prompt)
استخدمه أول مرة تفتح فيها المشروع.

```text
From today you are my video editor. I'm a [niche] creator; my audience is [who], and I speak
[language/dialect]. I film vertical talking-head reels on my phone while reading a script from a
tablet. Build me a local pipeline: I drop a raw clip in inbox/, you produce a finished
1080x1920 reel in out/. Use Python + ffmpeg, faster-whisper for transcription, MediaPipe for face
tracking, and Remotion for motion graphics. Create a rules file you read at the start of every
session and update whenever I correct you.
```

**بيعمل إيه؟** بيعرّفه بيك وبشغلته، ويخليه يبني الـ pipeline كله وملف الـ rules.

### 🎨 2. الألوان
```text
Here is a reference frame whose colour I want. Measure the wall, the skin (on the face itself,
using face landmarks) and the black level on the reference and on my footage, then build a grade
that matches. Show me both side by side before you render.
```

**بيعمل إيه؟** بيقيس الألوان بالأرقام على وشك انت مش على حتة ثابتة، ويوريك قبل وبعد جنب بعض.

### 💬 3. الـ Captions
```text
Captions: one word at a time, [colour], [font], centred on my chest, in [dialect], never formal
language. Any word I say in English stays written in English. Here is a reel whose captions I like.
```

**بيعمل إيه؟** بيظبط شكل الـ captions ومكانها، ويمنعه يكتب فصحى أو يعرّب الكلام الإنجليزي.

### ✨ 4. الـ Graphics
```text
Look at these reels. Write down the rules of their motion graphics as a design system (colours,
fonts, spacing, how things enter and exit). Then, for my reel, make one animated graphic per
phrase that shows exactly what I'm saying at that moment, starting on the word I say it.
No invented text, no unrelated logos.
```

**بيعمل إيه؟** بيحوّل الريلز اللي بتحبها لـ design system مكتوب، وبعدين يعمل graphic لكل جملة على التوقيت بالظبط.

### 📌 5. خلّي التصحيح يثبت
```text
Save this correction to your rules file and enforce it in code where you can, so you never make
this mistake again.
```

**بيعمل إيه؟** ده أهم Prompt في الموضوع كله. استخدمه بعد **كل** تصحيح.

### 💾 6. احفظ الـ Skill
```text
We've reached the look I want. Save everything we agreed on — the workflow, the rules, the
design system — as a reusable skill, so every new reel comes out like this on the first try.
```

**بيعمل إيه؟** بيقفل كل اللي اتعلمه في skill واحدة تستخدمها مع كل ريل جديد.

---

## 🇪🇬 تقدر تكتبله بالمصري كمان

```text
من النهارده انت المونتير بتاعي. أنا بعمل ريلز عن [الموضوع] لجمهور [مين]، وبتكلم مصري.
ابنيلي pipeline: أرمي الفيديو الخام في inbox/، وانت تطلّعلي ريل جاهز 1080x1920 في out/.
اقطع السكوت وأي لحظة ببص فيها على الـ script، بس عمرك ما تقص كلمة بقولها.
اعمل ملف rules تقراه أول كل session، وتضيف فيه أي تصحيح أقولهولك.
```

---

## 📄 ملف الـ Rules بتاعك — هيكل تبدأ بيه

Claude Code بيقرا ملف `CLAUDE.md` في أول المشروع مع بداية كل session. ابدأ بحاجة زي دي، وسيبها تكبر مع كل تصحيح:

```markdown
# My reel editor

## What this is
Raw clips go in inbox/, finished 1080x1920 reels come out in out/.

## Workflow
1. transcribe  2. face-track (cut look-downs)  3. write the edit file
4. check every graphic matches the words  5. render  6. look at frames  7. deliver

## Standing rules (from me — non-negotiable)
1. Captions: [your style]. Dialect, never formal. English words stay English.
2. Never cut a word I say. Cut only silences, stutters and real retakes.
3. Every glance at my script is cut.
4. My face is never covered by a graphic.
5. Every graphic shows exactly what I'm saying, timed to my words.
6. Colour: matched to [your reference]. Check it side by side.
7. Export: 1080x1920, square pixels, bt709.
<!-- add a rule every time you correct something -->
```

---

## ⚠️ دروس اتعلمناها بالطريقة الصعبة

- **اعرف الفيديو بتاعك HDR ولا SDR قبل ما تلعب في الألوان.** الـ iPhone غالباً بيصوّر HDR (HLG)، بس مش دايماً. LUT اتعمل على فيديو HDR حط بقع خضرا على حيطة رمادي وبقعة برتقاني على الجبهة لما اشتغل على فيديو SDR. `ffprobe` بيقولك انت عندك إيه (`color_transfer`).
- **قيس الجلد على الوش، مش على حتة ثابتة.** مربع ثابت قاس pixels غلط، فالأرقام قالت "مظبوط" والوش طالع باهت ومخضر. استخدم نقط الوش (face landmarks).
- **الأرقام لوحدها مش كفاية؛ بص على الصورة.** دايماً قارن الـ frames جنب الـ reference.
- **Whisper بيمط الكلمات على السكوت.** الكلمة ممكن "تبدأ" قبل ما تقولها بثانية، فبتستخبى جواها سكتة. ظبط بداية ونهاية كل كلمة على الصوت الحقيقي (silence detection).
- **متقصّش زيادة.** مرة الـ look-down detection كان عنيف لدرجة إنه حوّل take 3 دقايق لـ 34 ثانية وجمل كاملة اختفت. اقطع السكوت، مش الكلام.
- **اربط الـ graphics بالكلمات، مش بالتوقيت.** لما القص يتغير، الـ graphics بتتحرك معاه.
- **graphic واحدة في المرة، وعمرها ما تغطي الوش.** استخدم layout الـ graphics فيه ليها مكانها (مثلاً الـ graphics فوق، وانت في card تحت).
- **لوجوهات حقيقية، screenshots حقيقية، أرقام حقيقية.** متعملش mockup لشاشة منتج ومتألفش إحصائية. متحطش رقم على الشاشة غير لو تقدر تثبته.
- **لو استخدمت كليبات creators تانيين كـ reference:** اعمل blur للوشوش وخبّي الـ handles والـ URLs.
- **Instagram:** ارفع من **Create reel**؛ الـ "Create post" العادي بيرفض الـ 9:16.

---

## ✅ Checklist قبل ما تنشر

- [ ] كل جملة كنت عايزها لسه موجودة، ومفيش حاجة مقطوعة في نص كلمة
- [ ] مفيش ولا بصّة على الـ script فاضلة
- [ ] الـ captions بالمصري، والكلام الإنجليزي إنجليزي، ومفيش حاجة مغطية وشك
- [ ] كل graphic بتظهر على الكلمة اللي بتشرحها
- [ ] الألوان ماشية مع الـ reference لما تقارنهم جنب بعض
- [ ] الـ hook مقروء في أول 3 ثواني
- [ ] الـ end card فيه نفس كلمة الكومنت اللي بتقولها في الفيديو بالظبط
- [ ] الـ export 1080×1920، 9:16، bt709
- [ ] الرد الأوتوماتيك على كلمة الكومنت جاهز قبل ما تنشر

---

## 🚀 الخلاصة

| قبل | بعد |
|---|---|
| ساعات مونتاج لكل ريل | ترمي الفيديو في `inbox/` وتراجع |
| مونتير بيخمّن الـ style بتاعك | rules مكتوبة بتتنفذ كل مرة |
| نفس الغلطات بتتكرر | كل تصحيح بيتحفظ وميتكررش |
| graphics عامة | graphic لكل جملة على الكلمة بالظبط |

---

## ❓ أسئلة بتتسأل كتير

**لازم أكون developer؟**
لأ. محتاج توصف انت عايز إيه وتدّي feedback واضح. Claude Code هو اللي بيكتب الـ code ويشغّله.

**الريل بياخد قد إيه؟**
أول كام ريل بياخدوا وقت لأنك بتعلّمه الـ style بتاعك. بعد كده، معظمه وقت الـ render + مراجعتك.

**ممكن آخد الـ skill أو الـ templates بتاعتك؟**
لأ، وانت أصلاً مش عايزهم: نسخة من style حد تاني بتبان نسخة. الـ guide ده فيه كل اللي تحتاجه عشان تبني بتاعك.

**Vida AI ممكن تعمل ده للبيزنس أو البراند بتاعي؟**
أيوه. ابعت DM على [@steventawfik](https://www.instagram.com/steventawfik).

---

لو استفدت، تابعني عشان فيه Prompts وأتمتة أكتر جاية 🔥

**Steven Ayman — Vida AI**

<sub>اتعمل بـ Claude Code من Vida AI. الـ guide ده بيشارك طريقة؛ مفيهوش skill files خاصة، أو templates، أو brand assets، أو فيديوهات.</sub>
