# Архитектура RiversTun

## Общая схема

```
┌─────────────────────┐
│     Vue Frontend    │  ← Кент
│  (кнопки, список,   │
│   настройки)        │
└──────────┬──────────┘
           │ invoke()
           ▼
┌─────────────────────┐
│   Tauri Commands    │  ← Ты (Rust)
│  connect()          │
│  disconnect()       │
│  get_status()       │
│  import_link()      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│     Xray-core       │  (sidecar)
│  (запущенный процесс)│
└─────────────────────┘
```

## Основные команды (которые нужно реализовать в Rust)

```rust
#[tauri::command]
async fn connect(config: String) -> Result<(), String>

#[tauri::command]
async fn disconnect() -> Result<(), String>

#[tauri::command]
async fn get_status() -> Result<Status, String>

#[tauri::command]
async fn import_link(link: String) -> Result<Server, String>
```

## Sidecar

Xray-core будет лежать в `src-tauri/binaries/`  
Имя файла должно соответствовать требованиям Tauri (с target triple).
