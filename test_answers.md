# Техническая поддержка web-приложений (простой - codepen)

---

## Вопрос 1

**Задача:** На сервере переполнился диск. Как это проверить через командную строку без графической оболочки?

**Ответ:**

```bash
df -h          # показывает использование диска в human-readable формате
du -sh /*      # показывает размер всех директорий в корне
du -sh /path   # размер конкретной директории
df -i          # показывает использование inodes
```

---

## Вопрос 2

**Задача:** Исправить вёрстку трёх таблиц, чтобы первая строка заголовка (с названием таблицы) расширилась на все колонки.

**Ответ:**

```html
<table class='mytable'>
    <thead>
        <tr>
            <th colspan="3">countries</th>
        </tr>
        <tr>
            <th>ID</th>
            <th>Country</th>
            <th>Capital</th>
        </tr>            
    </thead>
    <tbody>
        <tr class='odd'>
            <td>1</td>
            <td>Canada</td>            
            <td>Ottawa</td>            
        </tr>        
        <tr>
            <td>2</td>
            <td>France</td>            
            <td>Paris</td>            
        </tr>
        <tr class='odd'>
            <td>3</td>
            <td>Germany</td>            
            <td>Italia</td>            
        </tr>
        <tr>
            <td>4</td>
            <td>Italy</td>            
            <td>Rome</td>            
        </tr>
        <tr class='odd'>
            <td>5</td>
            <td>Russian Federation</td>            
            <td>Moscow</td>            
        </tr>
        <tr>
            <td>6</td>
            <td>Spain</td>            
            <td>Madrid</td>            
        </tr>
        <tr class='odd'>
            <td>7</td>
            <td>United Kingdom</td>            
            <td>London</td>            
        </tr>
    </tbody>
</table>

<table class='mytable' id='users'>
    <thead>
        <tr>
            <th colspan="5">users</th>
        </tr>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>IsActor</th>
            <th>IsSinger</th>
            <th>Age</th>            
        </tr>            
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Adriano Celentano</td>  
            <td>1</td>
            <td>1</td>
            <td>82</td>
        </tr>                
        <tr>
            <td>2</td>
            <td>David Tennant</td>            
            <td>1</td>
            <td>0</td>
            <td>48</td>
        </tr>        
        <tr>
            <td>3</td>
            <td>Jean Reno</td>            
            <td>1</td>
            <td>0</td>
            <td>63</td>
        </tr>
        <tr>
            <td>4</td>
            <td>Till Lindemann</td>            
            <td>0</td>
            <td>1</td>
            <td>51</td>
        </tr>
        <tr>
            <td>5</td>
            <td>Jim Carrey</td>            
            <td>1</td>
            <td>0</td>
            <td>53</td>
        </tr>
        <tr>
            <td>6</td>
            <td>Gérard Xavier Marcel Depardieu</td>            
            <td>0</td>
            <td>1</td>
            <td>64</td>
        </tr>
        <tr>
            <td>7</td>
            <td>Олег Табаков</td>            
            <td>1</td>
            <td>0</td>
            <td>82</td>
        </tr>
    </tbody>
</table>

<table class='mytable' id='correspondence'>
    <thead>
        <tr>
            <th colspan="2">citizenship</th>
        </tr>
        <tr>
            <th>user_id</th>
            <th>country_id</th>
        </tr>            
    </thead>
    <tbody>
        <tr>
            <td>6</td>
            <td>5</td>            
        </tr>
        <tr>
            <td>1</td>
            <td>4</td>            
        </tr>        
        <tr>
            <td>3</td>
            <td>6</td>            
        </tr>
        <tr>
            <td>4</td>
            <td>3</td>            
        </tr>
        <tr>
            <td>2</td>
            <td>7</td>            
        </tr>
        <tr>
            <td>6</td>
            <td>2</td>            
        </tr>
        <tr>
            <td>5</td>
            <td>1</td>            
        </tr>
        <tr>
            <td>3</td>
            <td>2</td>            
        </tr>
        <tr>
            <td>7</td>
            <td>5</td>            
        </tr>
    </tbody>
</table>
```

---

## Вопрос 3

**Задача:** Добавить одно CSS-правило для подсветки нечётных строк в первой таблице цветом #e7e7e7.

**Ответ:**

```css
.mytable:first-of-type tbody tr:nth-child(odd) {
    background-color: #e7e7e7;
}
```

---

## Вопрос 4

**Задача:** Сделать так, чтобы форма сразу отправлялась при переходе на страницу без действий пользователя.

**Ответ:**

Добавить в HTML:

```html
<body onload="document.getElementById('formId').submit()">
```

или в JavaScript:

```javascript
window.onload = function() {
    document.querySelector('form').submit();
};
```

---

## Вопрос 5

**Задача:** Написать SQL-запрос, который выведет имена всех актёров.

**Ответ:**

```sql
SELECT Name FROM users WHERE IsActor = 1;
```

**Результат:**
- Adriano Celentano
- David Tennant
- Jean Reno
- Jim Carrey
- Олег Табаков

---

## Вопрос 6

**Задача:** К каким IP-адресам из списка НЕ получится подключиться извне?

**IP-адреса:**
- 151.248.113.78
- 127.0.0.1
- 194.85.283.12
- 192.168.15.2
- 172.16.0.9
- 185.76.145.0
- 10.55.84.56

**Ответ:**

Невозможно подключиться к:
| IP | Причина |
|----|---------|
| 127.0.0.1 | localhost (всегда локальный) |
| 192.168.15.2 | частный IP (диапазон 192.168.0.0/16) |
| 172.16.0.9 | частный IP (диапазон 172.16.0.0/12) |
| 10.55.84.56 | частный IP (диапазон 10.0.0.0/8) |

Можно подключиться к:
- 151.248.113.78 (публичный)
- 194.85.283.12 (публичный)
- 185.76.145.0 (публичный)