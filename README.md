# feature-sliced

<!-- 🏅 Add badges -->

<!--
[npm]: https://www.npmjs.com/package/NPM_PACKAGE

[![npm](https://img.shields.io/npm/v/NPM_PACKAGE?style=flat-square)][npm]
[![npm](https://img.shields.io/npm/dw/NPM_PACKAGE?style=flat-square)][npm]
[![npm bundle size](https://img.shields.io/bundlephobia/min/NPM_PACKAGE?style=flat-square)][npm]
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2FOWNER%2FREPO&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=true)](https://hits.seeyoufarm.com)
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/OWNER/REPO/WORKFLOW?label=tests&style=flat-square)](https://github.com/OWNER/REPO/actions)
[![GitHub commit activity](https://img.shields.io/github/commit-activity/m/OWNER/REPO?style=flat-square)](https://github.com/OWNER/REPO/commits)
-->

<!-- 🖼️ Add logo / primary image -->
<img src="https://avatars.githubusercontent.com/u/60469024?s=120" align="right" width=120>

<!-- ⚡ Add primary information & features about your repository -->
Методология, помогающая определять разбиение модулей и связи между ними в приложении

- Обеспечивает [**понятность и явность архитектуры**](https://github.com/feature-sliced/wiki/blob/master/about/architecture.md#explicit-%D0%BF%D0%BE%D0%BD%D1%8F%D1%82%D0%BD%D0%BE%D1%81%D1%82%D1%8C%D1%8F%D0%B2%D0%BD%D0%BE%D1%81%D1%82%D1%8C)
- Обеспечивает [**контроль и изоляцию модулей**](https://github.com/feature-sliced/wiki/blob/master/about/architecture.md#control-%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%BE%D0%BB%D1%8C%D0%B8%D0%B7%D0%BE%D0%BB%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D0%BE%D1%81%D1%82%D1%8C)
- Обеспечивает [**адаптивность под проекты**](https://github.com/feature-sliced/wiki/blob/master/about/architecture.md#adaptivity-%D0%B0%D0%B4%D0%B0%D0%BF%D1%82%D0%B8%D0%B2%D0%BD%D0%BE%D1%81%D1%82%D1%8C%D0%BA%D0%B0%D1%81%D1%82%D0%BE%D0%BC%D0%B8%D0%B7%D0%B8%D1%80%D1%83%D0%B5%D0%BC%D0%BE%D1%81%D1%82%D1%8C)

## Overview

Методология помогает *определять и стандартизировать разбиение модулей для больших и долгоживужих проектов.*

В соответствие с ней, становится проще поддерживать и адаптировать изменяющуюся функциональность приложений.

> См. также ["Требования к архитектуре"](./about/architecture.md)

### Мотивация

Стандартизация проектных знаний и решений, подкрепленная обширным опытом разработки.

Методология агрегирует лучшие практики и паттерны проектирования, с адаптацией под специфику разработки фронтенд-проектов *(базируясь на разделении ответственности модулей)*

> Ведь практик и паттернов много *(SOLID, GRASP, DDD)*, но устоявшиеся и конкретные подходы - крайне трудно найти

> См. также ["Мотивация создания методологии"](./about/motivation.md)

### Концепции

[`Public API`](./concepts/public-api.md), [`Isolation`](./concepts/cross-communication.md), ...

## Структура

> См. также ["Абстракции методологии"](./intro/abstractions.md) и ["Разбиение приложения"](./concepts/app-splitting.md)

> `WIP:` Нейминг групп временный, и будет определен окончательно ближе к релизу MVP

```sh
└── src/
    ├── app/                    # Layer: Приложение
    |                           #
    ├── processes/              # Layer: Процессы (опционален)
    |   ├── {some-process}/     #     Slice: (н-р процесс CartPayment)
    |   |   ├── lib/            #         Segment: Инфраструктурная-логика (хелперы)
    |   |   └── model/          #         Segment: Бизнес-логика
    |   ...                     #
    |                           #
    ├── pages/                  # Layer: Страницы
    |   ├── {some-page}/        #     Slice: (н-р страница ProfilePage)
    |   |   ├── lib/            #         Segment: Инфраструктурная-логика (хелперы)
    |   |   ├── model/          #         Segment: Бизнес-логика
    |   |   └── ui/             #         Segment: UI-логика
    |   ...                     #
    |                           #
    ├── features/               # Layer: Фичи
    |   ├── {some-feature}/     #     Slice: (н-р фича AuthByPhone)
    |   |   ├── lib/            #         Segment: Инфраструктурная-логика (хелперы)
    |   |   ├── model/          #         Segment: Бизнес-логика
    |   |   └── ui/             #         Segment: UI-логика
    |   ...                     #
    |                           #
    ├── entities/               # Layer: Бизнес-сущности
    |   ├── {some-entity}/      #     Slice: (н-р сущность User)
    |   |   ├── lib/            #         Segment: Инфраструктурная-логика (хелперы)
    |   |   ├── model/          #         Segment: Бизнес-логика
    |   |   └── ui/             #         Segment: UI-логика
    |   ...                     #
    |                           #
    ├── shared/                 # Layer: Переиспользуемые ресурсы
    |   ├── api/                #         Segment: Логика запросов к API
    |   ├── lib/                #         Segment: Инфраструктурная-логика (хелперы)
    |   └── ui/                 #         Segment: UI-логика
    |   ...                     #
    |                           #
    └── index.tsx/              #
```

## P.S. **Это не "серебряная пуля"**

Не так много примеров проектов, которые полностью следуют правилам и принципам методологии, с сохранением преимуществ

Это связано с тем, что принципы вырисовывают **очень идеальную** архитектуру в теории, но сложную в реализации

> На данный момент ведется активная работа над тем, чтобы соединить опыт многих разработчиков и выразить его в единой методологии, помогающей в реализации методологии в проектах

## См. также

<!--
TODO: Если ссылок будет потом оч много - вынести в переменные
-->

<!-- 
TODO: Перенести ссылки на референсы в /src/readme.md, как Карина добьет свой PR
-->

- `Get started` [Введение в методологию](./intro/readme.md)
- `About` [О методологии](./about/readme.md)
- `Misc` Прочие материалы
  - [A feature based approach to React development](https://ryanlanciaux.com/blog/2017/08/20/a-feature-based-approach-to-react-development/)
  - [Why React developers should modularize their applications?](https://alexmngn.medium.com/why-react-developers-should-modularize-their-applications-d26d381854c1)
  - [How to Organize Your React + Redux Codebase](https://www.pluralsight.com/guides/how-to-organize-your-react-+-redux-codebase)
  - [The Humanizing Work Guide to Splitting User Stories *(aka "Vetical Slices")*](https://www.humanizingwork.com/the-humanizing-work-guide-to-splitting-user-stories/)
  - [Доклад React SPB Meetup#1 - Feature Slices](https://t.me/feature_slices)
  - [Feature Driven Architecture - Oleg Isonen](https://www.youtube.com/watch?v=BWAeYuWFHhs)
  - *Предыдущие* ответвления методологии: *[feature-slices](https://featureslices.dev/v1.0.html)*, *[feature-driven](./about/old/feature-driven/README.md)*

<br/>

- `Discussions` [Дискуссии по методологии](https://github.com/feature-sliced/wiki/discussions)
  > **Здесь обсуждаются и разбираются рельные примеры применения, вопросы, проблемы, идеи методологии**
  >
  > Все это в совокупности влияет на спецификацию, тулкит и в целом - на дальнейшее видение и развитие методологии
  >
  > *Т.е. все, чего пока нет в спецификации/тулките - так или иначе обсуждается в github-discussions*
- `Contributing` **Как можно помочь?**
  - ⭐ Оцените нас на GitHub, если у вас остались положительные впечатления
    > Или если по-вашему этот проект должен развиваться дальше
  - 💫 Ознакомьтесь с нашим [contributing](./CONTRIBUTING.md) гайдом
    > **Важно любое содействие** - от *фидбека* до *участия в самой разработке!*

<!-- 
FIXME: Не удалось нормально justify-content:space-around применить в md
Если есть варики как лучше отступы расставить - welcome :)
-->

<!-- TODO: Добавить ссылкии, как доработаем ютуб и твиттер -->

<div align="center">

[![tg](./assets/social_tg.png)](https://t.me/feature_sliced "Телеграм-чат")
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[![twitter](./assets/social_twitter.png)](#wip "Twitter (в процессе)")
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[![open-collective](./assets/social_opencollective.png)](https://opencollective.com/feature-sliced "OpenCollective профиль")
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[![youtube](./assets/social_youtube.png)](#wip "YouTube канал (в процессе)")
</div>
