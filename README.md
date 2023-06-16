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

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Суфиксът е `.mdt` , можете да използвате синтаксиса, подобен на `<+ ./coffee_plus/import.js>` , за да препращате към външни файлове и да генерирате маркдаун с наставката `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Преводът на Markdown няма да превежда кодове и връзки и ще кешира преведените изречения. Ако преводът е променен, но оригиналният текст не е променен, повторното му изпълнение няма да презапише промяната на превода.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Езикови файлове за превод на уебсайтове, генерирани от `yaml` .

### Инструкции за автоматизиране на превода на документи

Вижте хранилището [xxai-art/doc](https://github.com/xxai-art/doc)

Препоръчително е първо да инсталирате nodejs, [direnv](https://direnv.net) и [bun](https://github.com/oven-sh/bun) и след това да стартирате `direnv allow` след влизане в директорията.

За да избегна прекалено големи складове, преведени на стотици езици, създадох отделно хранилище на кодове за всеки език и създадох организация за съхраняване на това хранилище

Задаването на променливата на средата `GITHUB_ACCESS_TOKEN` и след това стартирането [на create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) автоматично ще създаде склад.

Разбира се, можете да го поставите и в склад.

Препратка към скрипт за превод [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Кодът на скрипта се интерпретира, както следва:

[bunx](https://bun.sh/docs/cli/bunx) е заместител на npx, който е по-бърз. Разбира се, ако нямате инсталиран bun, можете да използвате `npx` вместо него.

`bunx mdt zh` изобразява `.mdt` в директорията zh като `.md` , вижте 2-та свързани файла по-долу

* [кафе_плюс.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` е основният код за превод (ако имате инсталирани само `nodejs` , но `bun` и `direnv` не са инсталирани, можете също да стартирате `npx i18n` за превод).

Той ще анализира [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , конфигурацията на `i18n.yml` в този документ е както следва:

```
en:
zh: ja ko en
```

Значението е: превод от китайски на японски, корейски, английски, превод от английски на всички други езици. Ако искате да поддържате само китайски и английски, можете просто да напишете `zh: en` .

Последният е [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , който извлича съдържанието между основното заглавие и първия подзаглавие на `README.md` на всеки език, за да генерира запис `README.md` . Кодът е много прост, можете да го разгледате сами.

Google API се използва за безплатен превод. Ако нямате достъп до Google, моля, конфигурирайте и задайте прокси, като например:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Скриптът за превод ще генерира кеш за превод в директория `.i18n` , моля, проверете го с `git status` и го добавете към хранилището на кода, за да избегнете повтарящи се преводи.
