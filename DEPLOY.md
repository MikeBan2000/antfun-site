# Деплой Antfun на GitHub + Cloudflare Pages

Пошаговая настройка: правки локально → push → сайт обновляется сам.

---

## 1. Git в папке проекта

В папке `C:\code\antfun` открой терминал (PowerShell или cmd) и выполни:

```powershell
cd C:\code\antfun
git init
git add index.html styles.css images/
git add .gitignore
git commit -m "Antfun site: initial"
```

(Если хочешь включить в репозиторий и бэкапы — замени на `git add .` и при необходимости поправь `.gitignore`.)

---

## 2. Репозиторий на GitHub

1. Зайди на [github.com](https://github.com), войди в аккаунт.
2. **New repository** → имя, например `antfun-site`.
3. **Public**, без README / .gitignore (у тебя уже есть локально).
4. На странице нового репо скопируй URL, например:  
   `https://github.com/ТВОЙ_ЛОГИН/antfun-site.git`

В терминале:

```powershell
git remote add origin https://github.com/ТВОЙ_ЛОГИН/antfun-site.git
git branch -M main
git push -u origin main
```

(Логин и имя репо подставь свои.)

---

## 3. Cloudflare Pages

1. Зайди в [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages**.
2. **Create** → **Pages** → **Connect to Git**.
3. Выбери **GitHub** и репозиторий `antfun-site`.
4. Настрой сборку:
   - **Production branch**: `main`
   - **Build command**: пусто (статический сайт)
   - **Build output directory**: `./` или `.`
5. **Save and Deploy**.

Сайт будет по адресу вида: `https://antfun.pages.dev`.

---

## 4. Свой домен (DNS)

В проекте Pages → **Custom domains** → добавь свой домен и настрой DNS по подсказкам Cloudflare.

---

## 5. Как обновлять сайт

После правок в коде:

```powershell
cd C:\code\antfun
git add .
git commit -m "Update: описание"
git push
```

Через 30–60 секунд изменения появятся на сайте.
