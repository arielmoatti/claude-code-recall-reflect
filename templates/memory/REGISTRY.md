# REGISTRY — זיהויים של <שם הפרויקט>

**מה נכנס כאן:** כל ה-IDs הגולמיים של הפרויקט — מספרי תרחישים, base/table IDs, connection IDs, webhooks, credentials, קודי מוצר, URLs ספציפיים ללקוח.

**חשוב:** תמיד תן כינוי (alias) קריא לכל ID. בשאר קבצי הזיכרון (למשל `ARCH_PATTERNS.md`) הפנה דרך הכינוי, לא דרך ה-ID הגולמי. ככה אם ID מתחלף, צריך לעדכן מקום אחד בלבד.

---

## Scenarios (Make.com / Boost.space)

<!-- דוגמה:
- **OnboardingFlow** — #9012345 — תרחיש קבלת לקוחות חדשים
- **DailyDigest** — #9023456 — תקציר יומי לצוות
-->

## Bases / Tables (Airtable, Boost.space)

<!-- דוגמה:
- **CustomersBase** — `appXXXXXXXXXXXXXX`
  - `Customers` — `tblAAAAAAAAAAAAAA`
  - `Orders` — `tblBBBBBBBBBBBBBB`
-->

## Connections

<!-- דוגמה:
- **MainSlack** — `__IMTCONN__123456`
-->

## Webhooks

<!-- דוגמה:
- **IntakeForm** — `https://hook.eu1.make.com/abc...` — מופעל כששולחים את טופס ההצטרפות
-->

## Credentials / Secrets

<!-- אל תכתוב credentials ממשיים כאן אם הפרויקט ציבורי ב-git. הפנה למיקום מקומי:
- **API token** — מאוחסן ב-`~/.claude/credentials/<project>.env` → `CLIENT_API_TOKEN`
-->

## URLs / Dashboards

<!-- דוגמה:
- **Admin panel** — `https://app.example.com/admin`
- **Logs** — `https://logs.example.com/project/xyz`
-->
