# АНАЛИЗ СОВРЕМЕННЫХ САЙТОВ 
## ЛАБОРАТОРНАЯ РАБОТА №10 по дисциплине «Веб-технологии»
**Выполнил**: Студент группы 241-672 Минеева Д. А.
### 1. Анализ сайтов и свойств
    
#### 1.1 Подборка сайтов
- BASARAB - интернет-магазин брендовой обуви, [BASARAB](https://basarab.ru/), интернет-магазин обуви;
- Магазин мужских костюмов и аксессуаров, [goodmens](https://good-mens.com/), интернет-магазин мужской одежды;
- Интернет-магазин «Армия России», [armrus](https://armrus.ru/), интернет-магазин одежды, сувениров;
- Официальный сайт производственного холдинга SKY FISH, [fishmarket](https://fishmarket.ru/), информационный сайт производственного холдинга;
- ПАО «Газпром», [gazprom](https://www.gazprom.ru/), информационный сайт Газпрома;
- Официальный сайт «KITFORT», [kitfort](https://kitfort.ru/), интернет-магазин бытовой техники;
- Третьяковская галерея, [treryakovgallery](https://www.tretyakovgallery.ru/?lang=ru), информационный сайт Третьяковской галереи;
- SELA, [sela](https://www.sela.ru/), интернет-магазин одежды;
- ЗОЛОТОЕ ЯБЛОКО, [goldapple](https://goldapple.ru/), интернет-магазин косметики;
- Недвижимость в Москве - новостройки от застройщика ЛСР, [lsr](https://www.lsr.ru/msk/), коммерческий сайт застройщика.

#### 1.2 Свойства
|№ | Синтаксис (правила) значения, прочая информация | Назначение | Где встретилось (ссылка на страницу сайта) |
|--| ----------------------------------------------- | ---------- | ------------------------------------------ |
|1.| unicode-bidi: [normal, embed, bidi-override, isolate, isolate-override, plaintext, initial, inherit] | Правильное отображение контента независимо от направления письма. | [BASARAB](https://basarab.ru/) |
|2.| overflow-x: [visible, hidden, clip, scroll, auto] | Обработка переполнения элемента по горизонтали | [goodmens](https://good-mens.com/)
|3.| tab-size: [number, length, initial, inherit] | Установка ширины символа табуляции | [armrus](https://armrus.ru/) |
|4.| word-break: [normal, break-all, keep-all,  break-word, initial, inherit] | Установка переноса строки | [armrus](https://armrus.ru/) |
|5.| backface-visibility: [hidden, visible] | Определяет, должна ли быть видна обратная сторона элемента(зеркальное отражение передней стороны) | [fishmarket](https://fishmarket.ru/) |
|6.| aspect-ratio: width / height | Устанавливает соотношение сторон для элемента | [sela](https://www.sela.ru/) |
|7.| pointer-events: [auto, none, visiblePainted, visibleFill, visibleStroke, visible, painted, fill, stroke, all, initial, inherit] |  Устанавливает реакцию элемента на события, связанные с указателем | [lsr](https://www.lsr.ru/msk/) |
|8.| text-rendering: [auto, optimizeSpeed, optimizeLegibility, geometricPrecision, initial, inherit]| Предоставляет механизму рендеринга информацию о том, что нужно оптимизировать при рендеринге текста | [treryakovgallery](https://www.tretyakovgallery.ru/?lang=ru) |
|9.| outline: [outline-width, outline-style, outline-color, initial, inherit] | Определяет область контура вокруг элемента (линии, которая рисуется сразу за границей элемента) | [lsr](https://www.lsr.ru/msk/) |
|10.| visibility: [visible, hidden, collapse, initial, inherit] | Скрывает или показывает элемент (элемент всё также занимает место в потоке) | [goldapple](https://goldapple.ru/) |

### 2. Структура сайта
![BASARAB](/png/basarab.png) [BASARAB](https://basarab.ru/)
 шапка, подвал, основная часть, меню. и его свойства. Например: Меню фиксировано, показывается всегда вверху страницы. Это реализовано за счет свойства display: fixed; Содержимое сайта выровнено по центру за счет указания ширины (width: 1020px) и свойства margin: 0 auto; 5.

 Шапка прозрачная, при наведении курсора становится белой. Свойство - position: fixed
 ```
 .header:not([data-view=static]) {
    position: fixed;
    }
 ```

 Подвал. Элементы при наведении курсора за 0,3 секунды окрашиваются в фиолетовый цвет
 с помощью свойства transition
 ```
 .footer-nav__link {
    color: currentColor;
    transition: .3s ease-in-out;
 }
 ```

 Основная часть. Карточки товаров расположены в одну строку и четыре колонны с помощью grid:
 ```
 .card-item__gallery-item-wrap {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(1px, 1fr));
 }
 ```

 Меню находится в шапке сайта. Внутренние отступы слева и справа размером 12 пикселей для пунктов меню только в том случае, если ширина экрана устройства составляет не менее 1440 пикселей. С помощью медиа-запроса @media only screen and (min-width: 1440px)
 ```
 @media only screen and (min-width: 1440px) {
    .header-nav__item {
        padding: 0 12px;
    }
}
 ```

![goodmens](/png/good-mens.png) [goodmens](https://good-mens.com/)

шапка имеет тень. Свойство - box-shadow. Шапка зафиксирована. Свойство - position: fixed
 ```
 header {
    position: fixed;
    box-shadow: 0px 4px 32px 0px #0000001F;
}
 ```

 Подвал. Элементы расположены по колоннам с помощью свойства flex-direction
 ```
 footer {
    display: flex;
    flex-direction: column;
 }
 ```

 Основная часть. Карточки товаров не сжимаются, то есть не игнорируют заданные размеры. Свойство - flex-shrink
 ```
 .swiper-slide {
    flex-shrink: 0;
    width: 100%;
    height: 100%;
    position: relative;
    transition-property: transform;
}
 ```

 Меню находится в шапке сайта посередине, благодаря margin
 ```
 .container {
    max-width: 1370px;
    padding: 0 10px;
    margin: 0 auto;
    margin-top: 0px;
    margin-right: auto;
    margin-bottom: 0px;
    margin-left: auto;
}
 ```


![armrus](/png/armrus.png) [armrus](https://armrus.ru/)
Шапка на больших экранах больше 1260 пикселей сдвигается вверх и занимает меньше места из-за медиа-запроса:
```
@media (min-width: 1260px) { 
    .app-header { top: -40px; } 
}
```

Подвал имеет вертикальный фон, когда устройство с шириной 600 пикселей и меньше, а если больше, то горизонтальный фон
```
@media (min-width: 600px) {
    .app-footer {
        background-image: url(/img/pattern-large.webp);
    }
}
.app-footer {
    background-image: url(/img/pattern_mobile.webp);
}
```

Основная часть. Согласованность размеров обеспечивается благодаря свойству box-sizing: inherit (каждый элемент наследует настройки размера родительского элемента)
```
*, :after, :before {
    background-repeat: no-repeat;
    box-sizing: inherit;
}
```

Меню. Элементы расположены по центру из-за установленного в display inline-flex и align-items
```
.brnd-link {
    align-items: center;
    color: #000;
    display: inline-flex;
}
```

![fishmarket](/png/fishmarket.png) [fishmarket](https://fishmarket.ru/)
Шапка закреплена сверху сайта. Свойство - position: fixed
```
.section__header {
    position: fixed;
}
```

В подвале элементы контейнера flexbox располагаются вертикально, и при этом они не переносятся на новые строки, оставаясь на одной линии.
```
.footer__menu__list {
    position: relative;
    display: flex;
    flex-flow: column nowrap;
}
```

Основная часть. При прокрутке страницы нижние изображения перекрывают начальное с помощью transform
```
element.style {
    translate: none;
    rotate: none;
    scale: none;
    transform: translate3d(0px, 208.487px, 0px);
}
```

Меню есть и в подвале, и в шапке сайта. Расстояние между элементами меню задаётся с помощью свойств:
```
.mob-menu__section .footer__menu__list {
    padding-top: .9166666667vw;
    margin-bottom: 1vw;
}
```

![gazprom](/png/gazprom.png) [gazprom](https://www.gazprom.ru/) 
Шапка имеет нижний отступ 40 пикселей. Свойство - padding-bottom
```
header {
    padding-bottom: 40px;
}
```

Подвал имеет отступ от основной части сайта. Свойство - padding-top
```
.footer .content_wrapper.inner {
    margin-top: 0;
    padding-left: 5%;
    padding-top: 100px;
}
```

Основная часть представлена блоками с отступом слева и изображениями на фоне.
```
@media screen and (max-width: 1280px) {
    .sheet {
        margin-left: 45%;
    }
}
```

Меню. Подзаголовки меню выделены
```
.menu-map__head {
    font-weight: 500;
}
```

![kitfort](/png/kitfort.png) [kitfort](https://kitfort.ru/)
Шапка. В ней основные элементы от элементов поддержки отделены с помощью space-between
```
.header__top {
    display: flex;
    justify-content: space-between;
}
```

Над подвалом находится черта - верхняя граница 
```
.main-footer__bottom .container-wide {
    border-top: 1px solid hsla(0, 0%, 100%, .7);
}
```

Основная часть. На одном из элементов курсор меняется на другой
```
.insta-choice__figure {
    cursor: url(../img/icons/icon-full-heart.png), auto;
}
```

Меню. При наведении курсора на элемент меню, цвет его фона меняется на фиолетовый
```
.header__menu-item:hover {
    background: #781ECD;
}
```

![treryakovgallery](/png/tretyakovgallery.png) [treryakovgallery](https://www.tretyakovgallery.ru/?lang=ru)
Шапка. Занимает 100% ширины экрана
```
.wrapper {
    width: 100%;
}
```

Подвал занимает 100% ширины экрана и имеет фон черного цвета
```
.footer {
    background: #000;
    width: 100%;
}
```

Основная часть. Пока экран больше 769 пикселей, отступ сверху и снизу будет 50 пикселей
```
@media (min-width: 769px) {
    .section {
        padding: 50px 0 50px;
    }
}
```

Меню. Ссылки находятся в рамках (border) и находятся рядом друг с другом в одной строке, имея фиксированные размеры и рамку
```
.btn {
    display: inline-block;
    outline: none;
    vertical-align: middle;
    text-align: center;
    border-radius: 0;
    text-shadow: none;
    cursor: pointer;
    text-decoration: none;
}
```

![sela](/png/sela.png) [sela](https://www.sela.ru/)
Шапка. Элементы располагаются в одной колонне
```
.header__menu {
    flex-direction: column;
}
```

Подвал. Подзаголовки капсом
```
.footer__list-name {
    text-transform: uppercase;
}
```

Основная часть. Баннеры переносятся на новую строку из-за свойства flex-wrap: wrap
```
.banners {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-bottom: 20px;
    width: 100%;
}
```

Меню имеет отступы 20 пикселей
```
.header__menu {
    padding: 20px;
}
```

![goldapple](/png/goldapple.png) [goldapple](https://goldapple.ru/)
Элементы шапки находятся в конце строки. Свойство - justify-content: flex-end
```
.ga-header__tabs {
    display: flex;
    justify-content: flex-end;
}
```

Подвал. Цвет и шрифт текста берутся от родительсих элементов из-заа свойства inherit
```
.uBWve {
    color: inherit;
    font-family: inherit;
}
```

Основная часть. Надписи на сменяющемся баннере появляются, потому что есть z-index: 1
```
._7y8wv {
    align-items: flex-end;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    justify-content: center;
    max-width: 1530px;
    width: 100%;
    z-index: 1;
}
```

Меню. Отступ сверху 20 пикселей
```
[dir] .evPhC {
    padding-top: 20px;
}
```

![lsr](/png/lsr.png) [lsr](https://www.lsr.ru/msk/)
Шапка. Отступ между элементами задан с помощью gap
```
.header__logoWrapper {
    --headerLogoWrapperGap: 2.5rem;
    align-items: center;
    display: flex;
    gap: var(--headerLogoWrapperGap);
}
```

Подвал. Задано количество и ширина колонок. Свойство - grid-template-columns
```
.footer__middleRowNav {
    display: grid;
    gap: var(--footerMiddleRowNavGap);
    grid-template-columns: var(--footerMiddleRowNavGridTemplateColumns);
}
```

Основная часть. Элементы (все, жилая, коммерческая, паркинги, кладовые) расположены в строчку с помощью display: flex;
```
.tabCheckerGroup {
    --tabCheckerGroupWidth: fit-content;
    --tagCheckerGroupItemPad: 1rem 2rem;
    --tabCheckerGroupItemBg: #0000;
    --tabCheckerGroupItemHoverBg: var(--colorWildSand);
    --tabCheckerGroupItemActiveBg: var(--colorGallery);
    --tabCheckerGroupColor: var(--colorMineShaft);
    border: 1px solid var(--colorAlto);
    border-radius: 4rem;
    display: flex;
    padding: 3px;
    width: var(--tabCheckerGroupWidth);
}
```

Меню. Плавный переход появления меню
```
.isDomReady .header__menuWrapper {
    transition: opacity .2s;
}
```

### 3. Реализация блока. Создание бегущей строки
![result](/png/result.png)
1. Создайте HTML-разметку для бегущей строки:
```
<div class="marquee-container">
    <div class="marquee-content">
        Бегущая строка: Привет, мир!
    </div>
</div>
```
2. Определите основные стили для контейнера бегущей строки:
```
.marquee-container {
    overflow: hidden;
    white-space: nowrap;
    width: 100%;
    background-color: #f0f0f0;
    font-size: 18px;
    line-height: 30px;
    height: 30px;
}
```
3. Добавьте стили для содержимого бегущей строки:
```
.marquee-content {
    animation: marquee 15s linear infinite;
    display: inline-block;
}
```
4. Опишите анимацию для содержимого строки:
```
@keyframes marquee {
    from { transform: translateX(100%); }
    to { transform: translateX(-100%); }
}
```
5. Убедитесь, что строка движется плавно:Анимация будет начинаться сразу, поэтому добавьте задержку для первого прохода:
```
.marquee-content {
    animation-delay: -7.5s;
}
```
6. Сделайте строку бесконечной:Чтобы строка двигалась непрерывно, добавьте вторую копию содержимого:
```
<div class="marquee-container">
    <div class="marquee-content">
        Бегущая строка: Привет, мир! Бегущая строка: Привет, мир!
    </div>
</div>
```
7. Отрегулируйте длину строки и скорость анимации:Скорость анимации зависит от длины текста и времени, за которое он проходит весь путь. Изменяйте время анимации и длину текста по необходимости.
Обеспечьте кроссбраузерность:Добавьте префиксы для ключевых кадров и анимации:
```
@-webkit-keyframes marquee {
    from { -webkit-transform: translateX(100%); }
    to { -webkit-transform: translateX(-100%); }
}

@-moz-keyframes marquee {
    from { -moz-transform: translateX(100%); }
    to { -moz-transform: translateX(-100%); }
}

@-o-keyframes marquee {
    from { -o-transform: translateX(100%); }
    to { -o-transform: translateX(-100%); }
}

.marquee-content {
    -webkit-animation: marquee 15s linear infinite;
    -moz-animation: marquee 15s linear infinite;
    -o-animation: marquee 15s linear infinite;
    animation: marquee 15s linear infinite;
}
```
8. Тестируйте результат:
Откройте страницу в браузере и убедитесь, что строка бежит корректно.
9. Настройка скорости движения:Вы можете изменить длительность анимации, чтобы увеличить или уменьшить скорость движения строки:
```
@keyframes marquee {
    from { transform: translateX(100%); }
    to { transform: translateX(-100%); }
}

.marquee-content {
    animation: marquee 10s linear infinite; /* Уменьшите время для ускорения */
}
```
10. Адаптация под мобильные устройства:Добавьте медиазапросы для корректного отображения на мобильных устройствах:
```
@media (max-width: 768px) {
    .marquee-container {
        font-size: 16px;
        line-height: 24px;
        height: 24px;
    }
}
```
11. Оптимизация производительности:Используйте will-change для улучшения производительности анимации:
```
.marquee-content {
    will-change: transform;
}
```
12. Добавление дополнительных эффектов:Можно добавить эффекты затухания начала и конца строки:
```
.marquee-container::before, .marquee-container::after {
    content: '';
    position: absolute;
    top: 0;
    width: 25%;
    height: 100%;
    background: linear-gradient(to right, rgba(240, 240, 240, 0), rgba(240, 240, 240, 1));
}

.marquee-container::after {
    right: 0;
    background: linear-gradient(to left, rgba(240, 240, 240, 0), rgba(240, 240, 240, 1));
}
```
13. Дополнительные настройки цвета и шрифтов:Настройте внешний вид строки по своему вкусу:
```
.marquee-container {
    background-color: #333;
    color: #fff;
    font-family: Arial, sans-serif;
}
```
14. Проверка совместимости:
Проверьте работу бегущей строки в различных браузерах и на разных устройствах.
Вот пример полного кода для реализации бегущей строки:
```
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Бегущая строка</title>
</head>
<body>
    <div class="marquee-container">
        <div class="marquee-content">
            Бегущая строка: Привет, мир! Бегущая строка: Привет, мир!
        </div>
    </div>
</body>
</html>
```
### Описание структуры сайта [BASARAB](https://basarab.ru/)
- HTML5 теги: современные HTML5 теги, такие как header, nav, main, section и footer.
- Классы CSS: используется БЭМ-нейминг в методологии классов. Они названы по смыслу содержимого и имеют часть для дальнейшей модификации, например about_btn element-animation, header-margin-top, produts_tape_wrap и так далее. Методология именования классов не строго соответствует какой-то конкретной системе, но имена интуитивно понятны и описывают назначение элементов.
- Использование обёрточных элементов div минимально и оправдано необходимостью группировки контента: в структуре используется до пяти уровней вложенности, что является достаточно типичным для веб-сайтов. Например, внутри секции header находится контейнер div class="header_new", а уже внутри него заголовки и текстовые блоки.
- Код хорошо структурирован и читаем, так как имена классов логичны и соответствуют назначению элементов.

### 4. Ресурсы
- [HTML, CSS](https://ru.w3docs.com/) - онлайн учебники и справочные материалы по HTML, CSS и JavaScript (решулярно обращаюсь во время выполнения работ)
- [справочник CSS](https://w3schools.tech/ru/tutorial/css/css_unicode-bidi) - справочник CSS (решулярно обращаюсь во время выполнения работ)
