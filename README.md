<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.чл

Част от кода на уебсайта е с отворен код, добре дошли да помогнете за оптимизирането на превода.

## преден код

* [преден код](https://github.com/xxai-art/web)
* [Езикови пакети за сайта като цяло](https://github.com/xxai-art/web/tree/main/i18n)
* [Езикови пакети за модули за вход](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Многоезична документация на уебсайта](https://github.com/xxai-doc)

Предният програмен език е [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , който добавя някои функции, базирани на синтаксиса на coffeescript, вижте [./coffee_plus.md](./coffee_plus.md) .

## Интернационализация на уебсайтове и документи

Надградете върху следните 3 проекта

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

Шаблонът за маркиране със суфикс `.mdt` може да препраща към външни файлове със синтаксис, подобен на `<+ ./coffee_plus/import.js>` .

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

Преводът на Markdown няма да превежда кодове и връзки и ще кешира преведените изречения. Ако преводът е променен, но оригиналният текст не е променен, повторното му изпълнение няма да презапише промяната на превода.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Езикови файлове за превод на уебсайтове, генерирани от `yaml` .
