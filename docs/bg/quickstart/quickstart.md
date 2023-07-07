# 1. Създайте нов проект

Целта на това ръководство за бърз старт е да ви предостави пълна настройка за разработка и напътствани стъпки за създаване на вашия първи блокчейн проект на SubQuery. Той е насочен към опитни разработчици до тези, които тепърва започват своето блокчейн пътуване.

Това ръководство за бърз старт трябва да отнеме около 10-15 минути.

След като завършите това ръководство за бърз старт, ще имате работещ проект на SubQuery, който ще се изпълнява на възел на SubQuery. Ще можете да адаптирате стандартния стартов проект и да индексирате трансфери от любимата си блокчейн мрежа като Polkadot, Avalanche, Cosmos и др.

Нека започнем процеса на създаване на вашия първи блокчейн проект SubQuery.

## Предпоставки

Преди да започнете да създавате първия си блокчейн проект с SubQuery, уверете се, че сте инсталирали необходимите поддържащи софтуерни приложения. Това са:

- [Node](https://nodejs.org/en/): Модерна (например LTS версия) инсталация на Node.
- [Docker](https://docker.com/): Този урок ще използва необходимия Docker.

Сега сте готови да започнете с първата стъпка, която е инсталирането на SubQuery CLI.

## 1. Инсталирайте SubQuery CLI

Инсталирайте SubQuery CLI глобално на вашият терминал с помощта на NPM:

```shell
# NPM
npm install -g @subql/cli
```

::: опасност Ние **НЕ** насърчаваме използването на `yarn global` за инсталиране на `@subql/cli` поради лошото му управление на зависимостите. Това може да доведе до множество грешки. :::

Разгледайте всички налични команди и тяхното използване. Изпълнете дадената по-долу команда в CLI:

```shell
subql help
```

## 2. Инициализиране на Стартов Проект в SubQuery

Изпълнете следната команда в директорията, в която искате да създадете проект на SubQuery:

```shell
subql init
```

Ще ви бъдат зададени определени въпроси, докато продължавате напред:

- **Име на проект**: Име на проект за вашия проект SubQuery.
- **Мрежово семейство**: Мрежовото семейство на блокчейн слой-1, което този проект на SubQuery ще индексира. Използвайте клавишите със стрелки, за да изберете от наличните опции. Например Polkadot, Avalanche, Cosmos или всяка друга поддържана мрежа.
- **Мрежа**: Конкретната мрежа, която този проект на SubQuery ще индексира. Използвайте клавишите със стрелки, за да изберете от наличните опции. Например Polkadot, Avalanche или всяка друга поддържана мрежа.
- **Шаблонен проект**: Изберете шаблонен проект на SubQuery, който ще предостави отправна точка в разработката. Предлагаме да изберете проекта _"subql-starter"_.
- **RPC endpoint**: Provide an HTTP or websocket URL to a running RPC endpoint, which will be used by default for this project. Можете бързо да осъществявате достъп до публични крайни точки за различни мрежи, да създадете свой собствен частен специализиран възел с помощта на [OnFinality](https://app.onfinality.io) или просто да използвате крайната точка по подразбиране. This RPC node must have the entire state of the data that you wish to index, so we recommend an archive node. Ще използваме стойността по подразбиране за това ръководство. В зависимост от мрежата, която сте избрали, стойността по подразбиране може да бъде:
  - For Polkadot - _"wss://polkadot.api.onfinality.io/public-ws"_,
  - For Avalanche - _"https://avalanche.api.onfinality.io/public/ext/bc/C/rpc"_,
  - For Ethereum - _“https://eth.api.onfinality.io/public”_ and likewise for other networks.
- **Git хранилище**: Предоставете Git URL към репо, в което този проект на SubQuery ще бъде хостван (когато се хоства в SubQuery Explorer), или приемете предоставеното по подразбиране.
- **Автори**: Въведете собственика на този проект на SubQuery тук (напр. вашето име!) или приемете предоставеното по подразбиране.
- **Описание**: Предоставете кратък абзац за вашия проект, който описва какви данни съдържа и какво потребителите могат да правят с него, или приемете предоставеното по подразбиране.
- **Версия**: Въведете персонализиран номер на версията или използвайте стандартната (`1.0.0`).
- **Лиценз**: Предоставете софтуерния лиценз за този проект или приемете стандартния (`MIT`).

Да разгледаме един пример:

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

След като завършите процеса на инициализация, ще видите папка с името на вашия проект, създадена вътре в директорията. Моля, обърнете внимание, че съдържанието на тази директория трябва да е идентично с това, което е посочено в [Структурата на директорията](../build/introduction.md#directory-structure).

Накрая изпълнете следната команда, за да инсталирате зависимостите на новия проект от директорията на новия проект.

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

There are 3 important files that need to be modified. Това са:

1. The GraphQL Schema in `schema.graphql`.
2. Манифест на проекта в `project.yaml`.
3. Mapping функциите в директорията `src/mappings/`.

SubQuery supports various blockchain networks and provides a dedicated guide for each of them. Select your preferred blockchain under **2. Specific Chains** and continue the quick start guide.
