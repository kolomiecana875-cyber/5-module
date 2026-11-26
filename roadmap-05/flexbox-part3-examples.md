# Flexbox: Практичні приклади та поради

## 1. Практичні приклади

### Навігаційне меню

```html
<nav class="menu">
  <a href="#" class="menu-item">Головна</a>
  <a href="#" class="menu-item">Про нас</a>
  <a href="#" class="menu-item">Послуги</a>
  <a href="#" class="menu-item">Контакти</a>
</nav>

<style>
.menu {
  display: flex;
  gap: 2rem;       /* Простір між елементами */
  justify-content: center;
  padding: 1rem;
  background: #f8f9fa;
}

.menu-item {
  padding: 0.5rem 1rem;
  text-decoration: none;
  color: #333;
  transition: color 0.3s;
}

.menu-item:hover {
  color: #007bff;
  background-color: rgba(0,123,255,0.1);
  border-radius: 4px;
}
</style>
```

### Картка товару

```html
<div class="product-card">
  <img src="product.jpg" alt="Product" class="product-image">
  <div class="product-content">
    <h3 class="product-title">Назва товару</h3>
    <p class="product-description">Опис товару...</p>
    <div class="product-footer">
      <span class="price">₴999</span>
      <button class="buy-button">Купити</button>
    </div>
  </div>
</div>

<style>
.product-card {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 300px;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.product-content {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.product-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: auto; /* Вирівнює футер внизу */
}

.buy-button {
  background: #4caf50;
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}
</style>
```

### Адаптивна сітка

```html
<div class="grid-container">
  <div class="grid-item">Елемент 1</div>
  <div class="grid-item">Елемент 2</div>
  <div class="grid-item">Елемент 3</div>
  <div class="grid-item">Елемент 4</div>
  <div class="grid-item">Елемент 5</div>
</div>

<style>
.grid-container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.grid-item {
  flex: 1 1 250px; /* Мінімальна ширина 250px */
  min-width: 0; /* Фікс проблеми переповнення */
  height: 150px;
  background-color: #f2f2f2;
  border-radius: 4px;
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
```

### Вертикальна центровка

```html
<div class="centered-box">
  <div class="content">
    Цей контент вертикально і горизонтально центрований
  </div>
</div>

<style>
.centered-box {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 300px;
  border: 2px solid #333;
}

.content {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
}
</style>
```

### Макет сторінки

```html
<div class="page-layout">
  <header class="header">Шапка сайту</header>
  <div class="main-content">
    <nav class="sidebar">Бічна панель</nav>
    <main class="content">Основний вміст</main>
  </div>
  <footer class="footer">Підвал сайту</footer>
</div>

<style>
.page-layout {
  display: flex;
  flex-direction: column;
  min-height: 100vh; /* Повна висота екрану */
}

.header, .footer {
  padding: 20px;
  background-color: #333;
  color: white;
}

.main-content {
  display: flex;
  flex: 1; /* Розтягується і займає весь доступний простір */
}

.sidebar {
  width: 250px;
  background-color: #f2f2f2;
  padding: 20px;
}

.content {
  flex: 1;
  padding: 20px;
}

/* Адаптивність для мобільних пристроїв */
@media (max-width: 768px) {
  .main-content {
    flex-direction: column;
  }
  
  .sidebar {
    width: 100%;
  }
}
</style>
```

## 2. Найкращі практики

### 1. Використання gap замість відступів

```css
/* ✔️ Правильно */
.container {
  display: flex;
  gap: 20px;
}

/* ❌ Застарілий підхід */
.item {
  margin-right: 20px;
}
.item:last-child {
  margin-right: 0;
}
```

### 2. Оптимізація flex-коефіцієнтів

```css
/* Гнучке зменшення/збільшення */
.item {
  flex: 1 1 200px; /* flex-grow | flex-shrink | flex-basis */
  min-width: 0; /* Виправлення переповнення */
}
```

### 3. Медіа-запити для адаптивності

```css
@media (max-width: 768px) {
  .container {
    flex-direction: column;
    gap: 10px;
  }
}
```

### 4. Вкладені контейнери

```html
<!-- Максимум 2-3 рівні вкладеності -->
<div class="flex-container">
  <div class="flex-item">
    <div class="nested-flex"><!-- ... --></div>
  </div>
</div>
```

## 3. Поширені помилки

### 1. Забутий flex-basis

```css
/* ❌ Проблема: може призвести до несподіваної поведінки */
.item {
  flex: 1;
}
/* ✔️ Виправлення: */
.item {
  flex: 1 1 0%; /* явно вказуємо flex-basis */
}
```

### 2. Конфлікт width і flex

```css
/* ❌ Суперечливі значення */
.item {
  width: 300px;
  flex: 1 1 auto;
}
/* ✔️ Оптимально: */
.item {
  flex: 1 1 300px; /* flex-basis замінює width */
}
```

### 3. Неправильний порядок властивостей

```css
/* ❌ Некоректний порядок */
.item {
  align-self: center;
  order: 2;
}
/* ✔️ Логічний порядок: спочатку порядок, потім вирівнювання */
.item {
  order: 2;
  align-self: center;
}
```

### 4. Зловживання !important

```css
/* ❌ Погана практика */
.item {
  flex-direction: column !important;
}
/* ✔️ Використовуйте специфічність селекторів */
.parent-container .item {
  flex-direction: column;
}
```

### 5. Ігнорування сумісності з браузерами

Хоча сучасні браузери добре підтримують Flexbox, для старих браузерів варто перевіряти сумісність або використовувати auto-prefixer:

```css
.container {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
}
```

## 4. Корисні ресурси

- [CSS-Tricks: Повний гайд Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Flexbox Froggy](https://flexboxfroggy.com/) - Інтерактивна гра для навчання
- [Flexbox Defense](http://www.flexboxdefense.com/) - Навчальна гра-стратегія
- [MDN Web Docs: Flexbox](https://developer.mozilla.org/uk/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
- [Flexbox Patterns](https://flexboxpatterns.com/) - Готові шаблони верстки
- [Can I Use: Flexbox](https://caniuse.com/flexbox) - Перевірка підтримки браузерами
- [Flexbugs](https://github.com/philipwalton/flexbugs) - Відомі проблеми та виправлення

## 5. Перехід до вивчення Grid Layout

Після освоєння Flexbox, наступним кроком є вивчення CSS Grid Layout, який ідеально підходить для складних двовимірних макетів.

Flexbox і Grid часто використовуються разом: Flexbox для однонаправлених макетів (рядків або колонок), а Grid для двовимірних макетів (рядків та колонок одночасно).
