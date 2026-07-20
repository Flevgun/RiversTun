# RiversTun

Простой и понятный десктоп-клиент для V2Ray / Xray (VLESS + Reality + VMess).

Сделан для обычных пользователей — минимум настроек, большой понятный интерфейс.

## Стек

- **Frontend**: Vue 3 + TypeScript + Vite
- **Backend**: Tauri 2 (Rust)
- **Ядро**: Xray-core (sidecar)

## Разделение работы

| Кто | За что отвечает | Папка |
|-----|------------------|-------|
| **Backend (ты)** | Запуск Xray, команды, sidecar, системный прокси, логика | `src-tauri/` |
| **Frontend (кент)** | Весь интерфейс, кнопки, список серверов, настройки | `src/` |

## Структура проекта

```
RiversTun/
├── src/                  # Frontend (Vue) - работает кент
│   ├── components/
│   ├── views/
│   ├── App.vue
│   └── main.ts
├── src-tauri/            # Backend (Rust) - работаешь ты
│   ├── src/
│   │   ├── main.rs
│   │   ├── commands.rs   # Команды для фронта (connect, disconnect и т.д.)
│   │   └── xray.rs       # Логика запуска Xray
│   ├── binaries/         # Сюда кладём xray.exe (sidecar)
│   ├── icons/
│   ├── Cargo.toml
│   └── tauri.conf.json
├── package.json
└── README.md
```

## Как начать работу

### 1. Установка зависимостей (нужно сделать один раз)

```bash
git clone https://github.com/Flevgun/RiversTun.git
cd RiversTun
npm install
```

### 2. Запуск в режиме разработки

```bash
npm run tauri dev
```

### 3. Сборка приложения

```bash
npm run tauri build
```

## Что уже нужно сделать

### Backend (приоритет)
- [ ] Настроить sidecar для Xray
- [ ] Команда `connect(config)`
- [ ] Команда `disconnect()`
- [ ] Команда `get_status()`
- [ ] Парсинг vless:// и vmess:// ссылок
- [ ] Системный прокси (Windows)

### Frontend
- [ ] Главный экран с большой кнопкой
- [ ] Список серверов
- [ ] Импорт ссылки / подписки
- [ ] Экран настроек
- [ ] Тёмная тема

## Полезные ссылки

- [Документация Tauri 2](https://v2.tauri.app)
- [Xray-core](https://github.com/XTLS/Xray-core)
- [Примеры sidecar](https://v2.tauri.app/develop/sidecar/)
