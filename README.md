# Создаем структуру файлов для готового сайта

import os
import zipfile

# Указываем директорию для файлов
base_path = "/mnt/data/ticket_site"
html_path = os.path.join(base_path, "index.html")
css_path = os.path.join(base_path, "styles.css")

# Создаем базовую структуру папки
os.makedirs(base_path, exist_ok=True)

# HTML-код для главной страницы
html_content = """
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Продажа билетов</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Онлайн-продажа билетов</h1>
        <nav>
            <ul>
                <li><a href="#events">Мероприятия</a></li>
                <li><a href="#about">О нас</a></li>
                <li><a href="#contact">Контакты</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="search">
            <h2>Найдите своё мероприятие</h2>
            <input type="text" placeholder="Поиск...">
            <button>Найти</button>
        </section>

        <section id="events">
            <h2>Популярные мероприятия</h2>
            <div class="event">
                <h3>Концерт группы "Название"</h3>
                <p>Дата: 15 декабря 2024</p>
                <p>Место: Москва</p>
                <button>Купить билет</button>
            </div>
            <div class="event">
                <h3>Театральная постановка "Ромео и Джульетта"</h3>
                <p>Дата: 20 декабря 2024</p>
                <p>Место: Санкт-Петербург</p>
                <button>Купить билет</button>
            </div>
        </section>
    </main>

    <footer>
        <p>© 2024 Онлайн-продажа билетов. Все права защищены.</p>
    </footer>
</body>
</html>
"""

# CSS-код для дизайна сайта
css_content = """
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #333;
    color: white;
    padding: 1rem 0;
    text-align: center;
}

header nav ul {
    list-style: none;
    padding: 0;
}

header nav ul li {
    display: inline;
    margin: 0 1rem;
}

header nav ul li a {
    color: white;
    text-decoration: none;
}

main {
    padding: 2rem;
}

#search {
    text-align: center;
    margin-bottom: 2rem;
}

#search input {
    padding: 0.5rem;
    width: 300px;
}

#search button {
    padding: 0.5rem 1rem;
    background-color: #333;
    color: white;
    border: none;
    cursor: pointer;
}

#events .event {
    border: 1px solid #ccc;
    padding: 1rem;
    margin: 1rem 0;
}

#events .event button {
    background-color: #333;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    cursor: pointer;
}

footer {
    background-color: #f4f4f4;
    text-align: center;
    padding: 1rem 0;
    margin-top: 2rem;
}
"""

# Записываем HTML и CSS в файлы
with open(html_path, "w", encoding="utf-8") as html_file:
    html_file.write(html_content)

with open(css_path, "w", encoding="utf-8") as css_file:
    css_file.write(css_content)

# Создаем ZIP-архив
zip_path = "/mnt/data/ticket_site.zip"
with zipfile.ZipFile(zip_path, "w") as zipf:
    zipf.write(html_path, "index.html")
    zipf.write(css_path, "styles.css")

zip_path
