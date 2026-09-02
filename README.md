# Сайт Никиты Бурлова на Quarto

Готовый стартовый статический сайт для редактирования в RStudio. R нужен только для постов с вычислениями; обычные страницы собирает Quarto.

## Быстрый старт в RStudio

1. Откройте файл `nikita-burlov-site.Rproj`.
2. В Terminal выполните `quarto preview` или нажмите **Render Website** в RStudio.
3. Quarto откроет локальную версию сайта и будет обновлять её после сохранения файлов.

## Что заменить перед публикацией

1. В `_variables.yml` замените все `USERNAME` на реальные адреса.
2. В `_quarto.yml` замените `site-url` на адрес GitHub Pages.
3. Перепишите вводный текст в `index.qmd`.
4. Замените `assets/profile-placeholder.svg` своей фотографией и измените путь к ней в `index.qmd`.
5. Замените демонстрационные публикации и отзывы.

## Новый пост

1. Скопируйте `templates/post-template.qmd` в новую папку вида `posts/2026-10-15-nazvanie/index.qmd`.
2. Положите изображения рядом с `index.qmd`.
3. Заполните YAML в начале файла: `title`, `description`, `date`, `categories`, `image`.
4. Удалите `draft: true`, когда пост готов.
5. Источники добавляйте в общий файл `references.bib`, а в тексте цитируйте как `[@citation-key]`.

Категории из поля `categories` автоматически появляются в фильтре блога.

## Новая научная публикация

Скопируйте блок из `templates/publication-template.md` в `publications.qmd` под нужный год. Библиографическое оформление остаётся обычным текстом, а DOI или PubMed добавляется ссылкой.

## Форма отзывов без собственного сервера

Использован Formspree — внешний сервис, который принимает HTML-форму и пересылает отзыв на подтверждённую почту.

1. Зарегистрируйтесь на [formspree.io](https://formspree.io/).
2. Создайте новую форму.
3. Скопируйте endpoint вида `https://formspree.io/f/xxxxxxxx`.
4. Вставьте его в `_variables.yml` вместо `https://formspree.io/f/REPLACE_WITH_FORM_ID`.
5. Отправьте тестовый отзыв с опубликованного сайта.

До замены endpoint форма отображается, но не доставляет сообщения. Formspree является отдельным обработчиком данных; при публикации стоит добавить собственный текст о конфиденциальности и проверить актуальные условия сервиса.

## Публикация на GitHub Pages

В проекте есть workflow `.github/workflows/publish.yml`.

1. Создайте репозиторий GitHub и загрузите туда проект.
2. Откройте **Settings → Pages**.
3. В разделе **Build and deployment → Source** выберите **GitHub Actions**.
4. Отправьте изменения в ветку `main`.
5. После завершения workflow сайт будет доступен по адресу GitHub Pages.

Если репозиторий называется `USERNAME.github.io`, адрес будет `https://USERNAME.github.io/`. Для обычного репозитория — `https://USERNAME.github.io/REPOSITORY/`.

## Структура

```text
.
├── _quarto.yml              # меню, формат, параметры сайта
├── _variables.yml           # все внешние ссылки и endpoint формы
├── index.qmd                # обо мне
├── blog.qmd                 # listing блога с фильтрами
├── publications.qmd         # публикации
├── journal-club.qmd         # журнальный клуб
├── services.qmd             # услуги и форма отзывов
├── contacts.qmd             # контакты
├── posts/                   # записи блога
├── templates/               # шаблоны поста и публикации
├── assets/                  # фото, favicon и другие ресурсы
├── references.bib           # общая библиография
└── styles.css               # дизайн
```
