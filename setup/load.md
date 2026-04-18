# Setup Wizard — `/load`

**מטרה:** להגדיר את פקודת `/load` של המשתמש וליצור `.claude/LOAD.md` בפרויקט הנוכחי (אופציונלי). קורא: Claude.

**תזכורת:** כל התקשורת עם המשתמש בעברית. אל תכתוב קובץ לפני אישור.

---

## שלב א' — בדיקת מצב קיים

כבר יש לך מידע מהסריקה ב-INSTALL.md. אם לא — סרוק עכשיו:

- `~/.claude/commands/load.md` — קיים?
- `<cwd>/.claude/LOAD.md` — קיים?

---

## שלב ב' — השאלה הראשונה (התנהגות לפקודה הקיימת)

**אם `~/.claude/commands/load.md` לא קיים:** דלג — לא צריך לשאול, פשוט כותבים חדש.

**אם `load.md` כבר קיים:** חובה להשתמש בכלי `AskUserQuestion` (חלונית popup מובנית של Claude Code), **לא** בטקסט רגיל. אם הכלי לא זמין ברשימה הישירה, קרא קודם ל-`ToolSearch` עם `select:AskUserQuestion` כדי לטעון את הסכמה. שאל:

> נמצא `~/.claude/commands/load.md` קיים. מה לעשות?
>
> - **החלף בגרסה החדשה** — תאבד את התוכן הישן, תקבל את הגרסה המותאמת של recall-reflect
> - **השאר את הקיים** — נדלג על הכתיבה הזאת
> - **הצג לי את שניהם** — תראה לי את הישן ואת המוצע, אני אחליט

**אם "הצג לי את שניהם"** — הראה דיף קצר (הקובץ הקיים מול תוכן הטמפלט `templates/load.md` מה-repo), ואז שאל שוב: "להחליף?"

---

## שלב ג' — כתיבת `~/.claude/commands/load.md`

אם המשתמש אישר החלפה (או אם לא היה קובץ קיים), משוך את התבנית:

```
https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/load.md
```

כתוב את התוכן ל-`~/.claude/commands/load.md`. **ללא שינויים** — התבנית אגנוסטית למשתמש ולא דורשת התאמה.

אם הכתיבה הצליחה, דווח בעברית: "✓ `~/.claude/commands/load.md` נכתב."

---

## שלב ד' — ארכיטקטורת תיעוד בפרויקט

**אם `<cwd>/.claude/LOAD.md` כבר קיים:** דלג על השלב הזה לגמרי. אמור למשתמש: "בפרויקט הזה כבר יש `.claude/LOAD.md`, לא נוגע בו." ועבור לפאזה הבאה.

**אם לא קיים:** חובה להשתמש בכלי `AskUserQuestion` (חלונית popup מובנית של Claude Code), **לא** בטקסט רגיל. אם הכלי לא זמין ברשימה הישירה, קרא קודם ל-`ToolSearch` עם `select:AskUserQuestion`. שאל:

> לא מצאתי `.claude/LOAD.md` בפרויקט הנוכחי (`<שם תיקייה>`). `/load` עובד הכי טוב כשיש מבנה זיכרון בנוי מראש — אחרת הוא מפנה לקבצים שלא קיימים. מה ליצור?
>
> - **ארכיטקטורה מלאה (מומלץ)** — LOAD.md מפורט + תיקיית `.claude/memory/` עם 5 קבצי שלד (MEMORY, REGISTRY, ARCH_PATTERNS, CURRENT_SPRINT, negative-knowledge) + `.claude/tmp/`. כל קובץ מגיע עם הסבר מה נכנס בו ותבנית פנימית.
> - **LOAD.md בלבד** — LOAD.md מפורט, בלי לייצר את קבצי הזיכרון. אתה תיצור אותם בעצמך לפי הצורך.
> - **דלג** — לא יוצר כלום עכשיו.

---

## שלב ה' — יצירת הקבצים (לפי הבחירה)

### אם "ארכיטקטורה מלאה":

משוך את הקבצים הבאים מה-repo וכתוב אותם למיקומים המתאימים:

| משוך מ- | כתוב ל- |
|---------|--------|
| `https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/LOAD.example.md` | `<cwd>/.claude/LOAD.md` |
| `https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/memory/MEMORY.md` | `<cwd>/.claude/memory/MEMORY.md` |
| `https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/memory/REGISTRY.md` | `<cwd>/.claude/memory/REGISTRY.md` |
| `https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/memory/ARCH_PATTERNS.md` | `<cwd>/.claude/memory/ARCH_PATTERNS.md` |
| `https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/memory/CURRENT_SPRINT.md` | `<cwd>/.claude/memory/CURRENT_SPRINT.md` |
| `https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/memory/negative-knowledge.md` | `<cwd>/.claude/memory/negative-knowledge.md` |

**בכל קובץ, החלף `<שם הפרויקט>`** בשם תיקיית ה-cwd האמיתי לפני כתיבה.

וודא שתיקיות `.claude/`, `.claude/memory/`, `.claude/tmp/` קיימות (צור אם חסרות). צור גם קובץ ריק `<cwd>/.claude/tmp/.gitkeep` כדי שתיקיית tmp תיכנס ל-git.

דווח בעברית:

```
✓ נוצרה ארכיטקטורה מלאה:
   .claude/LOAD.md
   .claude/memory/ (5 קבצים)
   .claude/tmp/
```

### אם "LOAD.md בלבד":

משוך את הגרסה המפורטת מה-repo:

```
https://raw.githubusercontent.com/arielmoatti/claude-code-recall-reflect/main/templates/LOAD.example.md
```

**החלף `<שם הפרויקט>`** בשם תיקיית ה-cwd האמיתי לפני כתיבה.

**הוסף בראש הקובץ (מתחת לכותרת) שורת הערה:**
```html
<!-- קבצי .claude/memory/ לא נוצרו על ידי האשף. צור אותם לפי הצורך לפני שתסתמך על LOAD.md כדי לטעון זיכרון. -->
```

וודא שתיקיית `.claude/` קיימת. כתוב את הקובץ.

דווח: "✓ `.claude/LOAD.md` נוצר. קבצי memory/ לא נוצרו — תיצור ידנית לפי הצורך."

### אם "דלג":

לא יוצר כלום. דווח: "דולג — לא נוצר LOAD.md. תוכל להריץ את ההתקנה שוב בעתיד, או ליצור ידנית."

---

## שלב ו' — סיום

אמור למשתמש:

> הגדרת `/load` הושלמה. כדי לבדוק: פתח שיחה חדשה עם Claude Code בתיקייה הזו והקלד `/load`. Claude אמור לקרוא את ה-LOAD.md ולדווח שהוא טעון.

חזור ל-INSTALL.md להמשך (Phase 3 — אשף `/burn`).
