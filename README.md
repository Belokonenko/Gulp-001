# Start Template: Gulp + WebPack + Babel

Сборку делал по примеру автора [youtube](https://www.youtube.com/watch?v=jU88mLuLWlk) 
канала: [Фрилансер по жизни](https://www.youtube.com/c/FreelancerLifeStyle)

## Для работы используйте такие команды

- Для установки всех зависимостей: `$ npm install`;
- Для запуска сборщика Gulp нужно использовать: `$ npm run dev`;
- Для сборки проекта в режиме `"production"`: `$ npm run build`;

## Что делает Gulp?

- сжимает HTML в режиме `production`;
- удаляет комментарии из HTML в режиме `production`;
- собирает SCSS файлы, добавляет вендорные префиксы;
- удаляет комментарии из SCSS файлов;
- в режиме `production` сжимает CSS и делает копию без сжатия;
- конвертирует шрифты в `.ttf`, и из `.ttf` в `woff/woff2`;
- создает файл для подключения шрифтов. Д
- анный файл создается по такому пути: `src/scss/config/fonts.scss`, 
- выглядит это так:

```scss
@font-face {
  font-family: Inter;
  font-display: swap;
  src: url('../fonts/Inter-Bold.woff2') format('woff2');
  font-weight: 700;
  font-style: normal;
}
```

### ВНИМАНИЕ!!!

> Если в папке `src/scss/config` - уже есть файл `fonts.scss` - тогда при добавлении новых шрифтов **НУЖНО УДАЛИТЬ** старый файл `fonts.scss`. Не переживай, при повторном запуске сборки - Gulp все новые шрифты сконвертирует и создаст новый файл `fonts.scss`.

Дальше, что еще умеет сборка:

- сжимает изображения и конвертирует их дополнительно в формат `.webp` и 
- подключает их если браузер поддерживает этот формат;
- 
- копирует папку `/static` с содержимым в финальную сборку. 
- То есть любые файлы можно поместить в эту папку и она будет добавлена в финальную 
- сборку без лишней обработки;
- 
- отдельной командой `$ npm run sprite` cоздает "svg cпрайты";
- перед каждым запуском сборщика чистит папку с финальным проектом, чтобы не собирать мусор;
- 
- отдельной командой `$ npm run zip` можно заархивировать финальную папку для 
- заказчика **с именем проекта**;
- 
- так же для разработки `gulp` запускает сервер с автоматической перезагрузкой окна в браузере при
- изменении файлов в проекте;
- 
- отдельной командой `$ npm run deployFTP` финальный проект выгружается на хостинг. 
- Опции для отправки проекта на нужный хостинг указываются в файле: `gulp/config/ftp.js`;
- 
- с 18.08.2023 есть поддержка шрифтов с такими названиями например: "`Inter-Regular[ |-|_|__][I|i]talic`" 
- - такие названия Gulp правильно обработает и запишет в стили `font-style: normal/italic`;
- 
- Конвертация шрифтов происходит в папке `src/fonts` 
- от туда шрифты с рассширением `.woff2` переносятся в `dist/fonts`. 
- Если файл для подключения шрифтов уже создан - 
- gulp просто перенесет шрифты `*.woff2` в `dist/fonts` без лишней трудозатратной конвертации.

## Что делает WebPack?

- именно `webpack` в данной сборке занимается обработкой файлов c JavaScript;
- поддерживается модульное подключение скриптов `import/export`;
- при импорте нет необходимости писать расширение файла `.js`, так 
- же если осуществляется импорт из файла `index.js` необязательно это указывать:

```javascript
import * as flsFunctions from './modules' // './modules/index.js'
```

- `webpack` c помощью `babel` позволяет тебе писать код на любимом **ES6+**;
- в режиме `"production"` при финальной сборке файлы JS сжимаются, а 
- лишние комментарии удаляются.

## Финал

Отдельной вишенкой является плагин `gh-pages` для деплоя папки `/dist` 
на отдельную ветку GitHub, чтобы красиво развернуть свой проект на GitHub Pages. 
Для этого в `package.json` укажи в поле **homepage** ссылку на свою страницу gh-pages:

```json
"homepage": "https://{UserName}.github.io/{NameRepo}",
```
"homepage": "https://github.com/Belokonenko/Gulp-001",

скопировал в браузере в адрес

По любым вопросам касающихся сборки пишите мне в [Telegram](https://t.me/StarkElessar).

.
├─ /dist
│   ├─ /css
│   ├─ /images
│   ├─ /js
│   ├─ index.html
│   └─ order.html
├─ /src
│   ├─ /components
│   │   ├─ /header
│   │   │   ├─ header.html
│   │   │   └─ header.scss
│   │   ├─ /offer
│   │   │   ├─ offer.html
│   │   │   ├─ offer.js
│   │   │   └─ offer.scss
│   │   ├─ /order
│   │   │   ├─ order.html
│   │   │   ├─ order.js
│   │   │   ├─ order.scss
│   │   └─ /footer
│   │       ├─ footer.html
│   │       ├─ footer.js
│   │       └─ footer.scss
│   ├─ /fonts
│   ├─ /images/Svg/
│   ├─ /icons(code svg for svgsprite)(not transferred)
│   ├─ /js
│   │   └─ pages
│   │       └─index.js
│   │       └─order.js
│   ├─ index.html
│   │─ order.html
│   └─ /scss
│       └─config/
│       │   └─ base.scss
│       │   └─ fonts.scss
│       └─libs/ 
│       └─ main.scss
├─ gulpfile.js
└─ package.json
