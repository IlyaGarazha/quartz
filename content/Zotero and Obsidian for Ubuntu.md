# Введение
Здравствуй, дорогой читатель! В этой статье я расскажу, как установить и использовать сборщик цитат и литературы [Zotero](https://www.zotero.org/)вместе с инструментом для [ведения](https://habr.com/ru/articles/710508/) заметок [Obsidian](https://obsidian.md/) на Ubuntu 22.04.

# Установка Obsidian
# Установка Zotero
1. Скачиваем [архив](https://www.zotero.org/download/)  (на текущий момент - Zotero-6.0.26_linux-x86_64.tar.bz2)
2. Распаковываем в ту папку, куда вам удобно (например `/opt/zotero`). 
3. Запускаем скрипт для установки иконки .desktop файла (`set_launcher_icon`)
4. Затем выполняем команду `ln -s /opt/zotero/zotero.desktop ~/.local/share/applications/zotero.desktop` (вместо /opt/zotero/ подставьте место, куда распаковали архив)
5. Проверяем, чтобы в файле `/home/username/.config/mimeapps.list` была строчка `x-scheme-handler/zotero=zotero.desktop;`
# Настройка Zotero

Скачиваем  и [устанавливаем](https://retorque.re/zotero-better-bibtex/installation/) расширение Better BibTex (Tools -> Add-ons -> ⚙️-> Install Add-on from file -> [файл .xpi](https://github.com/retorquere/zotero-better-bibtex/releases/tag/v6.7.116) ) 
![[1.png]]

# Настройка Obsidian

1. Устанавливаем (⚙️->Community plugins->Browse) плагин [Zotero integration](https://github.com/mgmeyers/obsidian-zotero-integration) 
![[Other/Hobby/My_articles/images/2.png]]
2. Переходим обратно в настройки и включаем плагин (4).
3. Переходим в раздел Zotero integration, добавляем PDF-utility, ждём пока скачается.
4. В поле Note Import  Location (3) указываем папку, в которой будут храниться наши ссылки на публикации.
 ![[3.png]]
 5. Создаём в папке с нашими ссылками файл Zotero_template.md следующего содержания: 
 ```
 --- Year: {{date | format("YYYY")}}
tags: Source 
Authors: {{authors}}{{directors}}
---

Title:: {{title}}
URL: {{url}}
Zotero Link: {{pdfZoteroLink}}


{% for annotation in annotations -%} 
    {%- if annotation.annotatedText -%} 
    {{annotation.annotatedText}}”{% if annotation.color %} {{annotation.colorCategory}} {{annotation.type | capitalize}} {% else %} {{annotation.type | capitalize}} {% endif %}[Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}) 
    {%- endif %} 
    {%- if annotation.imageRelativePath -%}
    ![[{{annotation.imageRelativePath}}]] {{"\n"}} [Page {{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}) 
{%- endif %} 
{% if annotation.comment %} 
{{annotation.comment}} 
{% endif %} 
{% endfor -%}

```
 7. Переходим к разделу Import Formats и добавляем новый формат (1) с названием формата (2), папку, где будут храниться наши файлы-ссылки и изображения, экспортируемые из Zotero (выделенная область PDF).  Указываем путь к нашему файлу Zotero_template.md (5).

![[4.png]]
### Настройка горячих клавиш
Community plugins -> Zotero integration -> + ->
![[7.png]]
# Использование
В Zotero добавляем необходимые pdf-файлы и делаем заметки, выделяем необходимые текст и  области (2).

![[8.png]]


После  чего, переходим в Obsidian и:
![Демонстрация работы](https://www.youtube.com/watch?v=zHUKgPBUC-w)

