# סט — התקנה כאפליקציה (GitHub Pages)

חבילה זו היא אפליקציית PWA. אחרי שמעלים אותה ל-GitHub Pages (HTTPS), אפשר להתקין אותה
על טאבלט הסמסונג כאפליקציה אמיתית — אייקון במסך הבית, מסך מלא, ועבודה גם ללא אינטרנט.

## קבצים בחבילה
- `index.html` — המשחק
- `manifest.json` — הגדרות האפליקציה (שם, אייקון, מסך מלא)
- `sw.js` — Service Worker (מאפשר התקנה ועבודה לא־מקוונת)
- `icon-192.png`, `icon-512.png` — אייקונים
- `README.md` — הקובץ הזה

> חשוב: להעלות את **הקבצים עצמם** לשורש ה-repo (כך ש-`index.html` בשורש),
> לא את התיקייה `pwa` שעוטפת אותם. הנתיבים בקבצים יחסיים, אז זה עובד גם בכתובת עם תת־נתיב.

## שלבים ב-GitHub Pages

1. צרי repo חדש (Public), למשל בשם `set-game`.
2. העלי את חמשת הקבצים (index.html, manifest.json, sw.js, icon-192.png, icon-512.png) לשורש ה-repo.
   - דרך הדפדפן: בעמוד ה-repo → **Add file → Upload files** → לגרור את הקבצים → **Commit changes**.
   - או ב-Git:
     ```
     git init
     git add .
     git commit -m "set game pwa"
     git branch -M main
     git remote add origin https://github.com/<USERNAME>/set-game.git
     git push -u origin main
     ```
3. ב-repo: **Settings → Pages**.
4. תחת **Build and deployment → Source** בחרי **Deploy from a branch**.
5. **Branch**: `main`, ותיקייה **/ (root)** → **Save**.
6. להמתין דקה. הכתובת תופיע למעלה, בצורה:
   `https://<USERNAME>.github.io/set-game/`

## התקנה על הטאבלט (Samsung)

1. פתחי את הכתובת `https://<USERNAME>.github.io/set-game/` בדפדפן **Chrome** בטאבלט.
2. תפריט ⋮ → **התקן אפליקציה** (או "הוסף למסך הבית") → אישור.
   - ב-Samsung Internet: תפריט ≡ → **הוסף דף אל → מסך הבית**, או אייקון ההתקנה בשורת הכתובת.
3. אייקון "סט" יתווסף למסך הבית וייפתח במסך מלא כמו אפליקציה.

## בדיקה מהירה שהכול תקין
- הכתובת מתחילה ב-`https://` (חובה ל-PWA).
- אין שגיאה 404 על `manifest.json` / `sw.js` (אפשר לבדוק ב-DevTools → Application).
- אם לא מופיע "התקן אפליקציה" מיד — רעני את העמוד פעם או פעמיים (ה-Service Worker נרשם בטעינה הראשונה).

## עדכון גרסה בעתיד
אחרי החלפת קבצים ב-repo, אם האפליקציה לא מתעדכנת — פתחי את הכתובת בדפדפן,
DevTools → Application → Service Workers → **Unregister**, ואז רענון. (או פשוט להעלות את המספר
בשורה `const CACHE = 'set-game-v1'` שב-`sw.js` לגרסה חדשה.)
