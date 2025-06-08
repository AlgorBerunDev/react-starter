# React TypeScript Starter 🚀

Профессиональный стартер для React проектов с TypeScript, настроенный с лучшими практиками разработки и автоматизацией.

## ✨ Особенности

- ⚡ **Vite** - быстрая сборка и разработка
- 🔷 **TypeScript** - типизация и современный JavaScript
- ⚛️ **React 18** - последняя версия React
- 🎯 **ESLint + Prettier** - качество и форматирование кода
- 🐕 **Husky** - автоматические Git hooks
- 📝 **CommitLint** - проверка Conventional Commits
- 🏷️ **Semantic Release** - автоматическое версионирование
- 🧪 **Vitest** - быстрое тестирование
- 📋 **lint-staged** - линтинг только измененных файлов
- 🔄 **GitHub Actions** - CI/CD pipeline

## 🚀 Быстрый старт

### Установка

```bash
# Клонирование репозитория
git clone https://github.com/AlgorBerunDev/react-starter.git
cd react-starter

# Установка зависимостей
npm install

# Запуск dev сервера
npm run dev
```

### Доступные команды

```bash
# Разработка
npm run dev          # Запуск dev сервера
npm run build        # Сборка для продакшена
npm run preview      # Просмотр production сборки

# Качество кода
npm run lint         # Проверка ESLint
npm run lint:fix     # Исправление ESLint ошибок
npm run format       # Форматирование с Prettier

# Тестирование
npm run test         # Запуск тестов в watch режиме
npm run test:ci      # Запуск тестов с coverage для CI
npm run test:ui      # Запуск Vitest UI

# Релизы
npm run semantic-release  # Создание релиза
```

## 📦 Структура проекта

```
react-starter/
├── .github/
│   └── workflows/
│       └── ci.yml           # GitHub Actions CI/CD
├── .husky/                  # Git hooks
│   ├── commit-msg          # Проверка commit сообщений
│   └── pre-commit          # Линтинг перед коммитом
├── public/                  # Статические файлы
├── src/
│   ├── assets/             # Изображения, иконки
│   ├── test/               # Настройки тестов
│   ├── App.tsx             # Главный компонент
│   ├── main.tsx            # Точка входа
│   └── vite-env.d.ts       # TypeScript определения Vite
├── .gitignore
├── .prettierrc             # Конфигурация Prettier
├── .releaserc.json         # Конфигурация Semantic Release
├── commitlint.config.js    # Конфигурация CommitLint
├── eslint.config.js        # Конфигурация ESLint
├── package.json
├── tsconfig.json           # TypeScript конфигурация
├── vite.config.ts          # Конфигурация Vite
└── vitest.config.ts        # Конфигурация Vitest
```

## 🔧 Конфигурация

### ESLint и Prettier

Проект настроен с строгими правилами ESLint и автоматическим форматированием Prettier. Конфигурация находится в:

- `eslint.config.js` - правила линтинга
- `.prettierrc` - настройки форматирования

### Husky и Git Hooks

Автоматические проверки при коммитах:

- **pre-commit**: запуск lint-staged для проверки измененных файлов
- **commit-msg**: проверка формата commit сообщений

### CommitLint

Проект использует [Conventional Commits](https://conventionalcommits.org/) стандарт:

```bash
# Примеры правильных коммитов
feat: add user authentication
fix: resolve login button styling issue
docs: update README with setup instructions
style: format code with prettier
refactor: extract utility functions
test: add unit tests for user service
chore: update dependencies
```

### Semantic Release

Автоматическое версионирование основано на типах коммитов:

- `feat:` → минорная версия (1.0.0 → 1.1.0)
- `fix:` → патч версия (1.0.0 → 1.0.1)
- `BREAKING CHANGE:` → мажорная версия (1.0.0 → 2.0.0)

## 🧪 Тестирование

Проект настроен с Vitest и Testing Library:

```bash
# Создание теста для компонента
# src/components/Button/Button.test.tsx
import { render, screen } from '@testing-library/react'
import { describe, it, expect } from 'vitest'
import Button from './Button'

describe('Button', () => {
  it('renders correctly', () => {
    render(<Button>Click me</Button>)
    expect(screen.getByRole('button')).toBeInTheDocument()
  })
})
```

## 🔄 CI/CD

GitHub Actions автоматически:

- Запускает линтинг и тесты на каждый PR
- Создает релизы при push в main/master ветку
- Публикует в GitHub Releases с автоматическим CHANGELOG

### Настройка для вашего проекта

1. **Форкните или клонируйте репозиторий**
2. **Обновите package.json**:
   ```json
   {
     "name": "your-project-name",
     "repository": {
       "type": "git",
       "url": "https://github.com/yourusername/your-repo.git"
     }
   }
   ```
3. **Настройте GitHub Actions права**:
   - Settings → Actions → General
   - Workflow permissions → "Read and write permissions"

## 📝 Рекомендации по разработке

### Структура компонентов

```typescript
// src/components/Button/Button.tsx
interface ButtonProps {
  children: React.ReactNode
  variant?: 'primary' | 'secondary'
  onClick?: () => void
}

export const Button: React.FC<ButtonProps> = ({
  children,
  variant = 'primary',
  onClick
}) => {
  return (
    <button
      className={`btn btn--${variant}`}
      onClick={onClick}
    >
      {children}
    </button>
  )
}

export default Button
```

### Типизация

```typescript
// src/types/index.ts
export interface User {
  id: string;
  name: string;
  email: string;
}

export interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
}
```

### Хуки

```typescript
// src/hooks/useApi.ts
import { useState, useEffect } from 'react';

export const useApi = <T>(url: string) => {
  const [data, setData] = useState<T | null>(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    // API логика
  }, [url]);

  return { data, loading, error };
};
```

## 🤝 Участие в разработке

1. Форкните проект
2. Создайте feature ветку (`git checkout -b feat/amazing-feature`)
3. Сделайте коммит (`git commit -m 'feat: add amazing feature'`)
4. Отправьте в ветку (`git push origin feat/amazing-feature`)
5. Откройте Pull Request

## 📄 Лицензия

MIT License. Смотрите [LICENSE](LICENSE) файл для подробностей.

## 📞 Поддержка

Если у вас есть вопросы или предложения:

- Создайте [Issue](https://github.com/AlgorBerunDev/react-starter/issues)
- Или отправьте Pull Request

---

**Создано с ❤️ для разработчиков React**
