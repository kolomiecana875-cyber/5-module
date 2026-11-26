# ⚡ Шпаргалка: Flexbox

Flexbox — це інструмент CSS для створення гнучких макетів, розподілу простору та вирівнювання елементів.

## 🏗️ 1. Властивості Контейнера (`display: flex;`)

| Властивість | Значення | Опис |
| --- | --- | --- |
| **`flex-direction`** | `row` (за зам.), `row-reverse`, `column`, `column-reverse` | Напрямок головної осі. |
| **`flex-wrap`** | `nowrap` (за зам.), `wrap`, `wrap-reverse` | Чи переносяться елементи на новий рядок. |
| **`gap`** | `10px`, `1rem 2rem` | Відступи між елементами. Краще, ніж `margin`! |

### Вирівнювання:
* **`justify-content`** (вздовж головної осі):
  `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`.
* **`align-items`** (вздовж поперечної осі):
  `stretch` (за зам.), `flex-start`, `flex-end`, `center`, `baseline`.
* **`align-content`** (багаторядкове вирівнювання, якщо є `flex-wrap: wrap`):
  `stretch`, `flex-start`, `flex-end`, `center`, `space-between`, `space-around`.

---

## 📦 2. Властивості Елементів (Flex Items)

| Властивість | Значення | Опис |
| --- | --- | --- |
| **`flex-grow`** | `0` (за зам.), `1`, `2`... | Чи розтягується елемент у вільному просторі. |
| **`flex-shrink`** | `1` (за зам.), `0`, `2`... | Чи стискається елемент при нестачі простору. |
| **`flex-basis`** | `auto` (за зам.), `200px`, `0` | Базовий розмір елемента до розподілу простору. |
| **`flex`** | `0 1 auto` (за зам.), `1`, `auto` | Скорочення: `flex-grow` `flex-shrink` `flex-basis`. |
| **`align-self`** | `auto`, `center`, `flex-start`... | Перевизначає `align-items` для окремого елемента. |
| **`order`** | `0` (за зам.), `1`, `-1` | Змінює порядок відображення (без зміни HTML). |

---

## 💡 3. Найкращі практики та підказки

1. **Використовуйте `gap`** замість зовнішніх відступів (`margin`) для створення проміжків між елементами.
2. **Типова комбінація для гнучкого елемента:** 
   `flex: 1 1 auto;` (дозволяє і стискатися, і розтягуватися).
3. **Вертикальна та горизонтальна центровка:**
   ```css
   .container {
     display: flex;
     justify-content: center;
     align-items: center;
   }
   ```
4. **Запобігання переповненню:**
   Щоб запобігти виходу тексту або вмісту за межі `flex-item`, додайте йому `min-width: 0;` (або `min-height: 0;` для колонок).
5. **Макет (Sidebar + Content):**
   ```css
   .main-content { display: flex; flex: 1; }
   .sidebar { width: 250px; }
   .content { flex: 1; }
   ```
