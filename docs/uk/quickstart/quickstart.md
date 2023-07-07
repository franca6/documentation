# 1. Створіть новий проєкт

Мета цього короткого керівництва по початку роботи надати вам повну настройку розробки й покрокові інструкції по створенню вашого першого проєкт блокчейн SubQuery. Він орієнтований на досвідчених розробників і тих, хто тільки починає свій шлях в блокчейнові.

Цей короткий посібник з початку роботи повинен зайняти близько 10-15 хвилин.

Після завершення цього короткого посібника у вас буде робочий проєкт SubQuery, який буде виконуватися на вузлі SubQuery. Ви зможете адаптувати стандартний стартовий проєкт і індексувати переклади з вашої улюбленої блокчейн-мережі, такий як Polkadot, Avalanche, Cosmos і т. д.

Почнім процес створення Вашого першого SubQuery блокчейн проєкту.

## Передумова

Перш ніж ви почнете створювати свій перший блокчейн проєкт за допомогою SubQuery, переконайтеся, що у вас встановлені необхідні допоміжні програмні додатки. Це:

- [Node](https://nodejs.org/en/): сучасна (наприклад, версія LTS) інсталяція Node.
- [Docker](https://docker.com/): У цьому посібнику буде використовуватися необхідний Docker.

Тепер ви все готові почати з першого кроку, який полягає в установці CLI SubQuery.

## 1. Встановити SubQuery CLI

Встановіть SubQuery CLI глобально на свій термінал за допомогою NPM:

```shell
# NPM
npm install -g @subql/cli
```

Небезпека! Ми **Не** заохочуємо використання `yarn global` для встановлення `@subql/cli` через його погане управління залежностями. Це може призвести до численних помилок. :::

Погляньте на всі доступні команди та їх використання. Виконайте наведену нижче команду в командному рядку:

```shell
subql help
```

## 2. Ініціалізуйте проект SubQuery Starter

Виконайте таку команду всередині каталогу, в якому ви хочете створити проєкту SubQuery:

```shell
subql init
```

У міру просування вперед вам будуть ставити собі певні питання:

- ** Project name **: ім'я проєкт для вашого проєкту SubQuery.
- ** Network family **: сімейство мереж блокчейн рівня 1, яке буде індексуватися цим проєкт SubQuery. Використовуйте клавіші зі стрілками, щоб вибрати один з доступних варіантів. Наприклад, Polka dot, Avalanche, Cosmos або будь-яка інша підтримувана мережа.
- **Network**: конкретна мережа, яку буде індексувати цей проєкт SubQuery. Використовуйте клавіші зі стрілками, щоб вибрати один з доступних варіантів. Наприклад, Polka dot, Avalanche або будь-яка інша підтримувана мережа.
- ** Template project **: Виберіть проєкт шаблону вкладеного запиту, який стане відправною точкою в розробці. Ми пропонуємо вибрати проєкт _"subql-starter"_.
- **RPC endpoint**: Provide an HTTP or websocket URL to a running RPC endpoint, which will be used by default for this project. Ви можете швидко отримати доступ до загальнодоступних кінцевих точок для різних мереж, створити свій власний приватний виділений вузол, використовуючи [OnFinality](https://app.onfinality.io), або просто використовувати кінцеву точку за замовчуванням. This RPC node must have the entire state of the data that you wish to index, so we recommend an archive node. У цьому посібнику ми будемо використовувати значення за замовчуванням. Залежно від вибраної вами мережі значення за замовчуванням може бути:
  - For Polkadot - _"wss://polkadot.api.onfinality.io/public-ws"_,
  - For Avalanche - _"https://avalanche.api.onfinality.io/public/ext/bc/C/rpc"_,
  - For Ethereum - _“https://eth.api.onfinality.io/public”_ and likewise for other networks.
- ** Git repository **: вкажіть URL-адресу Git для звіту, в якому буде розміщений цей проєкт SubQuery (при розміщенні в провіднику SubQuery), або прийміть вказане значення за замовчуванням.
- ** Authors **: введіть тут власника цього проєкту SubQuery (наприклад, ваше ім'я!) або прийміть вказане значення за замовчуванням.
- ** Description **: вкажіть короткий абзац про Ваш проєкт, в якому описується, які дані він містить і що користувачі можуть з ним робити, або прийміть надане значення за замовчуванням.
- ** Version **: введіть номер користувача версії або використовуйте значення за замовчуванням (`1.0.0`).
- ** License **: надайте ліцензію на програмне забезпечення для цього проєкту або прийміть стандартну (`MIT`).

Розгляньмо приклад:

```shell
$ subql init
Project name [subql-starter]: HelloWorld
? Select a network family Substrate
? Select a network Polkadot
? Select a template project subql-starter     Starter project for subquery
RPC endpoint: [wss://polkadot.api.onfinality.io/public-ws]:
Git repository [https://github.com/subquery/subql-starter]:
Fetching network genesis hash... done
Author [Ian He & Jay Ji]: Sean
Description [This project can be used as a starting po...]:
Version [1.0.0]:
License [MIT]:
Preparing project... done
HelloWorld is ready
```

Після завершення процесу ініціалізації ви побачите тека з ім'ям вашого проєкту, створену всередині каталогу. Будь ласка, зверніть увагу, що вміст цього каталогу має бути ідентичним тому, що вказано в [структурі каталогів](../build/introduction.md#directory-structure).

Нарешті, виконайте таку команду, щоб встановити залежності нового проєкту з каталогу нового проєкту.

::: code-tabs @tab:active yarn

```shell
cd PROJECT_NAME
yarn install
```

@tab npm

```shell
cd PROJECT_NAME
npm install
```

:::

You have now initialised your first SubQuery project with just a few simple steps. Let’s now customise the standard template project for a specific blockchain of interest.

You may want to refer to the [command line arguments](../run_publish/references.md) used in SubQuery. It will help you understand the commands better.

## 3. Make Changes to Your Project

There are 3 important files that need to be modified. Це:

1. The GraphQL Schema in `schema.graphql`.
2. Маніфест проєкту в `project.yaml`.
3. Функції відбивання в `src/mappings/` каталогу.

SubQuery supports various blockchain networks and provides a dedicated guide for each of them. Select your preferred blockchain under **2. Specific Chains** and continue the quick start guide.
