# 📷 Склад видеооборудования — Telegram Mini App

## Быстрый старт (3 шага)

---

### ШАГ 1 — Настройка базы данных Supabase

1. Откройте ваш проект на https://supabase.com
2. Перейдите в **SQL Editor** (левое меню)
3. Вставьте содержимое файла `supabase_setup.sql` и нажмите **Run**

Это создаст три таблицы (`users`, `equipment`, `lendings`) и бакет для фотографий.

---

### ШАГ 2 — Разместите index.html на GitHub Pages (бесплатно)

1. Создайте новый репозиторий на GitHub (например `video-warehouse`)
2. Загрузите `index.html` в корень репозитория
3. Перейдите в **Settings → Pages → Source → Deploy from branch → main**
4. Через 1-2 минуты приложение будет доступно по адресу:
   `https://ВАШ_НИК.github.io/video-warehouse/`

---

### ШАГ 3 — Подключите к Telegram боту

1. Откройте @BotFather в Telegram
2. Напишите `/newapp` (или `/setmenubutton`)
3. Выберите вашего бота
4. Введите URL из GitHub Pages как Web App URL
5. Готово! Нажатие на кнопку меню откроет приложение

---

### Настройка уведомлений для администраторов

В файле `index.html` найдите строку:
```js
const ADMIN_IDS = []; // добавьте ваш Telegram ID сюда
```

Замените на ваш Telegram ID (узнать можно у @userinfobot):
```js
const ADMIN_IDS = [123456789]; // ваш ID
```

После этого при каждой выдаче/возврате вы будете получать уведомления в Telegram.

---

## Возможности приложения

### Для сотрудников
- 📋 Список всего оборудования с фильтрами по категориям
- 🔍 Поиск по названию и инвентарному номеру
- 📷 Фото инвентарного номера при получении
- 🤖 **Автоматическое распознавание номера через Claude AI**
- 📦 Вкладка «У меня» — что взято сейчас
- ↩️ Быстрый возврат одним нажатием

### Для администратора
- ⚙️ Вкладка «Админ» со статистикой
- 📊 Журнал всех выдач и возвратов
- ➕ Добавление нового оборудования с фото
- 🔔 Push-уведомления в Telegram

---

## Структура базы данных

```
equipment
  id, name, category, inventory_number,
  inventory_photo_url, status, created_at

users  
  telegram_id, name, username, created_at

lendings
  id, equipment_id, user_telegram_id, user_name,
  taken_at, returned_at, photo_url, notes
```

---

## Технологии

- **Frontend**: чистый HTML/JS (без фреймворков)
- **База данных**: Supabase (PostgreSQL)
- **Хранилище фото**: Supabase Storage
- **OCR**: Claude claude-sonnet-4-20250514 Vision API
- **Хостинг**: GitHub Pages
- **Всё бесплатно** до ~50 активных пользователей
