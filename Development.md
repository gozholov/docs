# Разработка сайта «Тундра Парк»

Техническое описание текущего каркаса сайта.

## Стек

- Next.js 16 (App Router)
- React 19
- TypeScript
- Tailwind CSS 4
- nodemailer (отправка заявок)

## Структура проекта

```text
app/
  page.tsx              — главная страница
  layout.tsx            — обёртка, metadata
  globals.css           — базовые стили
  api/request/route.ts  — POST-обработчик заявки
components/
  HomePage.tsx          — вся вёрстка главной
data/
  home.ts               — программы, highlights, контакты
docs/                   — документация
yandex.env.local        — SMTP-секреты (в .gitignore)
```

## Запуск

```bash
npm install
npm run dev
```

Локальный адрес: `http://localhost:3000`

## Сборка

```bash
npm run build
npm start
```

## Отправка заявок

Форма отправляет POST на `/api/request`. Сервер читает SMTP из переменных окружения или `yandex.env.local`.

Формат `yandex.env.local`:

```env
SMTP_HOST=smtp.yandex.ru
SMTP_PORT=465
SMTP_USER=tundrapark@yandex.ru
SMTP_PASSWORD=пароль_приложения
MAIL_TO=tundrapark@yandex.ru
```

Важно:
- использовать пароль приложения Яндекс Почты, не обычный пароль;
- в настройках Яндекс Почты включить доступ для почтовых программ;
- файл `yandex.env.local` не коммитить (указан в `.gitignore`).

После изменения `yandex.env.local` перезапустить `npm run dev`.

## Главная страница

Реализованные блоки см. в `docs/context.md`.

Данные программ в `data/home.ts`:
- `season`: `winter` | `summer` | `all`
- `price`, `pricesBySeason` — цены
- `descriptionsBySeason` — разные описания по сезону

Логика сезона по умолчанию в `HomePage.tsx`: 01.05–30.09 = лето, иначе зима.

## Цвета (реализовано)

- тёмный фон: `#10201b`, `#132018`
- светлый фон: `#f4efe4`
- акцент: `#d9a456`
- шрифт: Arial

## Что ещё не сделано

1. Отдельные страницы программ.
2. Реальные изображения.
3. Админка / CMS для контента.
4. Мультиязычность.
5. SEO: sitemap, микроразметка.
6. Яндекс Метрика.
