# Приложение "Книжный компас"

### Структура проекта

```text
vue-project/                                 # Корень проекта Vue 3 + Vite
├── README.md                                # Документация проекта
├── index.html                               # HTML-шаблон, контейнер #app, подключение src/main.ts
├── package.json                             # Скрипты, зависимости и метаданные
├── package-lock.json                        # Лок-файл зависимостей npm
├── vite.config.ts                           # Конфиг Vite (алиас @→src, devtools отключены)
├── eslint.config.ts                         # ESLint (Vue + TS + Prettier skip-formatting)
├── tsconfig.json                            # Базовая конфигурация TypeScript
├── tsconfig.app.json                        # TS-конфиг приложения
├── tsconfig.node.json                       # TS-конфиг для Node-инструментов
├── env.d.ts                                 # Типы окружения Vite для импортов и .vue
├── vk-hosting-config.json                   # Конфиг деплоя для VK Mini Apps
├── public/                                  # Публичные ассеты, копируются как есть
│   └── favicon.ico                          # Иконка приложения
├── docs/                                    # Проектная документация (ADR, гайды, схемы)
└── src/                                     # Исходный код приложения
    ├── App.vue                              # Корневой компонент приложения
    ├── main.ts                              # Входная точка: VK Bridge init + тема, Pinia, Router
    ├── assets/                              # Стили и статические ресурсы
    │   └── tailwind.css                     # TailwindCSS (base/components/utilities)
    ├── components/                          # UI-компоненты
    │   ├── Navbar.vue                       # Нижняя навигация (4 вкладки, подсветка по route.name)
    │   └── ProfileCard.vue                  # Карточка профиля (аватар, имя, ID) + скелетон
    ├── router/                              # Маршрутизация приложения
    │   └── index.ts                         # Маршруты: home, search, cart, profile
    ├── stores/                              # Pinia-хранилища
    │   └── user.ts                          # Стор пользователя: UserInfo, setUser/clearUser
    └── views/                               # Страницы
        ├── HomeView.vue                     # Главная (использует ProfileCard/Pinia)
        ├── SearchView.vue                   # Поиск
        ├── CartView.vue                     # Корзина
        └── ProfileView.vue                  # Профиль
```

#### Примечания

- Алиас `@` указывает на каталог `src`.
- DevTools для Vue отключены в `vite.config.ts` (удалён `vite-plugin-vue-devtools`).
- Навигация учитывает нижний safe-area: `pb-[env(safe-area-inset-bottom)]`.
