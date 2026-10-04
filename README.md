# 💣 Сапёр

Классический «Сапёр» в стиле Windows на React и TypeScript: поле 16×16, 40 мин, счётчик флагов, таймер и тот самый смайлик.

**[🔗 Играть](https://sapper-danu-it.vercel.app)**

## Возможности

- Поле 16×16 с 40 минами, генерация случайная
- Первый клик безопасен: если он попал на мину, поле генерируется заново
- Автоматическое открытие пустых областей (flood fill на стеке, без рекурсии)
- Правый клик переключает состояние клетки: флаг → вопрос → пусто
- Счётчик оставшихся мин и таймер в «пиксельных» цифрах
- Смайлик реагирует на игру: 🙂 по умолчанию, 😲 при нажатии на клетку, 😵 при проигрыше, 😎 при победе. Клик по нему начинает новую игру
- При проигрыше открываются все мины

## Стек

![React](https://img.shields.io/badge/React_18-20232A?style=flat&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![styled-components](https://img.shields.io/badge/styled--components-DB7093?style=flat&logo=styled-components&logoColor=white)

- React 18 (хуки: `useState`, `useMemo`, `useEffect`)
- TypeScript
- styled-components
- Деплой на Vercel

## Как устроено

Поле хранится в двух плоских массивах длиной `size * size`:

- `field`: содержимое клетки (`-1` для мины, `0–8` для количества мин вокруг)
- `mask`: что видит игрок (закрыто, открыто, флаг, вопрос)

Мины расставляются в `createField`, и счётчики соседних клеток сразу увеличиваются. Победа вычисляется через `useMemo`: игра выиграна, когда все клетки без мин открыты.

## Запуск

```bash
git clone https://github.com/donuwave/sapper-react.git
cd sapper-react
npm install
npm start
```
