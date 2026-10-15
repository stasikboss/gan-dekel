# ועד גן דקל

אפליקציית ווב (PWA) לוועד ההורים של גן דקל: חלוקת אחריות, מתנות ומסיבות, תקציב וגבייה ל־18 ילדים, ורכש והחזרים ב־PayBox.
אפשר להתקין אותה למסך הבית בטלפון. הנתונים משותפים בין חברי הוועד בזמן אמת דרך Firebase.

## הפעלה (פעם אחת, כ־10 דקות)

1. **יצירת פרויקט Firebase:** ב־[console.firebase.google.com](https://console.firebase.google.com) צרו פרויקט חדש (התוכנית החינמית Spark מספיקה).
2. **Firestore:** Build → Firestore Database → Create database (מיקום `eur3` או `me-west1`).
3. **כניסה עם Google:** Build → Authentication → Get started → Sign-in method → Google → Enable.
4. **דומיין מורשה:** Authentication → Settings → Authorized domains → הוסיפו `stasikboss.github.io`.
5. **חוקי אבטחה:** העתיקו את `firestore.rules` אל Firestore → Rules, הוסיפו את המיילים של דסי, נילי וברכי, ולחצו Publish.
6. **Config:** Project settings → Your apps → Web app (`</>`), העתיקו את `apiKey`, `authDomain`, `projectId`, `appId` לקובץ `firebase-config.js` ועשו commit.

ה־apiKey של Firebase לא סודי. מה שמגן על הנתונים הוא חוקי ה־Firestore, שמאפשרים גישה רק למיילים שברשימה.

בכניסה הראשונה של חבר ועד מורשה, האפליקציה ממלאת את חלוקת האחריות והאירועים מהישיבה הראשונה.

## בלי Firebase

כל עוד `firebase-config.js` ריק, האפליקציה רצה במצב הדגמה ושומרת נתונים רק בדפדפן של המכשיר.

## GitHub Pages

Settings → Pages → Source: Deploy from a branch → `main` / root.
הכתובת: `https://stasikboss.github.io/gan-dekel/`

## קבצים

| קובץ | תפקיד |
|---|---|
| `index.html` | כל האפליקציה (HTML, CSS, JS) |
| `firebase-config.js` | הגדרות הפרויקט |
| `firestore.rules` | מי רשאי לקרוא ולכתוב |
| `manifest.webmanifest`, `sw.js`, `icons/` | התקנה למסך הבית ועבודה בלי רשת |
