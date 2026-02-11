# GitHub Pages Setup Instructions

## Шаг 1: Создать новый публичный репозиторий

1. Перейдите на GitHub: https://github.com/new
2. Название репозитория: `tarqatoo-legal`
3. Описание: `Legal documents for Tarqatoo app`
4. **Важно:** Выберите **Public** (публичный)
5. Нажмите **Create repository**

## Шаг 2: Загрузить файлы в репозиторий

### Вариант A: Через веб-интерфейс GitHub (проще)

1. Откройте созданный репозиторий на GitHub
2. Нажмите **Add file** → **Upload files**
3. Перетащите все файлы из папки `docs/legal/github-pages/`:
   - `index.html`
   - `terms.html`
   - `privacy.html`
   - `style.css`
4. Напишите commit message: `Initial commit: Add legal documents`
5. Нажмите **Commit changes**

### Вариант B: Через командную строку (для опытных)

```bash
# Перейдите в папку с файлами
cd /Users/kayumov/Projects/Tarqatoo/docs/legal/github-pages

# Инициализируйте Git
git init

# Добавьте все файлы
git add .

# Создайте коммит
git commit -m "Initial commit: Add legal documents"

# Подключите удалённый репозиторий
git remote add origin https://github.com/paradi2e/tarqatoo-legal.git

# Переименуйте ветку в main (если нужно)
git branch -M main

# Отправьте на GitHub
git push -u origin main
```

## Шаг 3: Включить GitHub Pages

1. В репозитории перейдите в **Settings** (⚙️)
2. Слева выберите **Pages**
3. В разделе **Source**:
   - **Branch**: выберите `main`
   - **Folder**: выберите `/ (root)`
4. Нажмите **Save**
5. Подождите 1-2 минуты

## Шаг 4: Получить ссылку на сайт

GitHub Pages автоматически опубликует сайт по адресу:

```
https://paradi2e.github.io/tarqatoo-legal/
```

Проверьте что страницы доступны:
- **Главная**: https://paradi2e.github.io/tarqatoo-legal/
- **Terms**: https://paradi2e.github.io/tarqatoo-legal/terms.html
- **Privacy**: https://paradi2e.github.io/tarqatoo-legal/privacy.html

## Шаг 5: Обновить ссылки в приложении

После того как GitHub Pages заработает, обновите URL в вашем приложении:

Откройте `Tarqatoo/Extensions/AppConstants.swift` и измените:

```swift
enum Legal {
    /// Terms of Service URL (GitHub Pages)
    static let termsOfServiceURL = "https://paradi2e.github.io/tarqatoo-legal/terms.html"

    /// Privacy Policy URL (GitHub Pages)
    static let privacyPolicyURL = "https://paradi2e.github.io/tarqatoo-legal/privacy.html"
}
```

## Шаг 6: Протестировать в приложении

1. Запустите приложение
2. Откройте Paywall экран
3. Нажмите на кнопки "Terms of Service" и "Privacy Policy"
4. Убедитесь что они открываются в Safari

---

## Будущее: Прикрепить свой домен (опционально)

Когда у вас будет хостинг на `tarqatoo.com`, вы сможете:

### Вариант 1: Использовать поддомен
- Настроить `legal.tarqatoo.com` → GitHub Pages
- В настройках DNS добавить CNAME запись:
  ```
  legal.tarqatoo.com → paradi2e.github.io
  ```
- В настройках GitHub Pages указать custom domain: `legal.tarqatoo.com`

### Вариант 2: Перенести на свой хостинг
- Скопировать все HTML файлы на свой сервер
- Разместить по адресу `https://tarqatoo.com/legal/`
- Обновить ссылки в `AppConstants.swift`

---

## Обновление документов в будущем

Когда нужно обновить документы:

1. Отредактируйте HTML файлы локально
2. Загрузите на GitHub (через веб или git push)
3. GitHub Pages автоматически обновится за 1-2 минуты
4. Изменения сразу отразятся в приложении (не нужен update приложения!)

---

## Проверка статуса GitHub Pages

После настройки можно проверить статус:
1. Settings → Pages
2. Вверху должно быть зелёное сообщение:
   ```
   ✓ Your site is published at https://paradi2e.github.io/tarqatoo-legal/
   ```

---

## Troubleshooting

**Проблема:** 404 Not Found
- Решение: Убедитесь что файлы в корне репозитория (не в подпапке)
- Решение: Подождите 5-10 минут, GitHub Pages может медленно обновляться

**Проблема:** Стили не применяются
- Решение: Проверьте что `style.css` загружен в репозиторий
- Решение: Откройте DevTools в браузере и проверьте Console на ошибки

**Проблема:** Приложение не может открыть ссылку
- Решение: Убедитесь что URL правильный в `AppConstants.swift`
- Решение: Проверьте что репозиторий публичный (Public)
