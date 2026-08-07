# Acme Financial Dashboard

![Next.js](https://img.shields.io/badge/Next.js-App_Router-black?logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?logo=typescript)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-06B6D4?logo=tailwindcss)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-4169E1?logo=postgresql&logoColor=white)

[English](#english) · [Українська](#українська)

## English

### About the project
## Live Demo
[View Live Site](https://nextjs-dashboard-coral-pi-63.vercel.app/)

Demo credentials:

Email: user@nextmail.com
Password: 123456

Acme Financial Dashboard is a full-stack application built while completing the official [Next.js App Router course](https://nextjs.org/learn/dashboard-app). It demonstrates a modern financial dashboard with authentication, protected routes, database-driven analytics, invoice management, search, pagination, validation, error handling, and responsive UI.

This repository documents not only the final result, but also the performance, user-experience, and developer-experience improvements introduced throughout all 16 course chapters.

### Try it out
To access the protected dashboard and explore the application pages, open the `/login` page and sign in with the demo credentials:

```text
Email: user@nextmail.com
Password: 123456
```
After signing in, you can explore the dashboard, customers, invoices, search and pagination, and the invoice creation and editing flows. You can also sign out when you finish reviewing the application.

### Main features

- Responsive public landing page and protected dashboard
- Credentials-based authentication and route protection
- Revenue overview, summary cards, and latest invoices
- PostgreSQL-backed data fetching
- Invoice search and URL-based pagination
- Create, edit, and delete invoice operations
- Server-side form validation with accessible error messages
- Streaming UI with route and component-level loading skeletons
- Route-level error recovery and custom `404` handling
- Optimized fonts, images, navigation, and metadata

### Tech stack

- Next.js with the App Router
- React and React Server Components
- TypeScript
- Tailwind CSS and CSS Modules
- PostgreSQL with the `postgres` client
- Auth.js / NextAuth.js
- Zod
- Heroicons, `clsx`, and `use-debounce`

### What I learned — all 16 course chapters

#### 1. [Getting Started](https://nextjs.org/learn/dashboard-app/getting-started)

I explored the project structure, reusable UI and utility folders, placeholder data, TypeScript definitions, and the local development workflow.

**Next.js improvement:** `create-next-app` provides an integrated, production-oriented foundation with App Router conventions, TypeScript support, optimized development tooling, and Turbopack. This reduces setup work and keeps the codebase organized from the beginning.

#### 2. [CSS Styling](https://nextjs.org/learn/dashboard-app/css-styling)

I used global styles, Tailwind CSS utilities, a scoped CSS Module, and `clsx` for conditional styles such as invoice statuses and active navigation links.

**Next.js improvement:** global styles are loaded once from the root layout, CSS Modules avoid naming collisions, and utility classes keep component styling colocated and responsive without growing a large hand-written stylesheet.

#### 3. [Optimizing Fonts and Images](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images)

I added Inter and Lusitana with `next/font`, responsive desktop and mobile hero images, and customer avatars with `next/image`.

**Next.js optimization:** fonts are downloaded at build time and self-hosted, avoiding extra browser requests and reducing layout shift. The Image component reserves image dimensions, supports responsive delivery, lazy loading, and modern image formats to improve loading performance and Core Web Vitals.

#### 4. [Creating Layouts and Pages](https://nextjs.org/learn/dashboard-app/creating-layouts-and-pages)

I created routes through the file-system convention and added a shared dashboard layout with persistent side navigation. The dashboard overview uses a route group so code can be organized without changing the URL.

**Next.js improvement:** nested layouts preserve shared UI between route changes, avoid unnecessary rerenders, and remove duplicated page structure. File-system routing makes the relationship between URLs and code explicit.

#### 5. [Navigating Between Pages](https://nextjs.org/learn/dashboard-app/navigating-between-pages)

I implemented navigation with `next/link` and highlighted the current dashboard route with `usePathname` and `clsx`.

**Next.js optimization:** the Link component enables client-side transitions and automatic route prefetching when links enter the viewport. Navigation feels faster because the browser does not perform a full page reload.

#### 6. [Setting Up Your Database](https://nextjs.org/learn/dashboard-app/setting-up-your-database)

I connected the application to PostgreSQL, defined users, customers, invoices, and revenue tables, and created a seed route using the provided placeholder data.

**Application improvement:** persistent relational data replaces hard-coded UI data. Parameterized SQL queries provide a reliable data layer, while the server-only database connection keeps credentials and database access out of the client bundle.

#### 7. [Fetching Data](https://nextjs.org/learn/dashboard-app/fetching-data)

I fetched dashboard and invoice data directly in async React Server Components. Related dashboard queries run concurrently with `Promise.all`, and SQL performs filtering, joins, ordering, aggregation, and pagination close to the data.

**Next.js optimization:** Server Components can query the database without a separate client API layer or additional browser requests. Less JavaScript is sent to the client, sensitive database logic stays on the server, and parallel queries reduce request waterfalls.

#### 8. [Static and Dynamic Rendering](https://nextjs.org/learn/dashboard-app/static-and-dynamic-rendering)

I learned to distinguish content that can be prepared ahead of time from request-dependent dashboard data. The authenticated dashboard and URL-driven invoice results are rendered from current request and database state.

**Next.js optimization:** static UI can be prepared and reused for speed, while dynamic rendering keeps personalized and frequently changing financial data accurate. Choosing the rendering strategy per route avoids making the entire application unnecessarily dynamic.

#### 9. [Streaming](https://nextjs.org/learn/dashboard-app/streaming)

I added a route-level `loading.tsx`, reusable skeletons, and component-level Suspense boundaries for cards, revenue, recent invoices, and the invoice table.

**Next.js optimization:** the page shell and available content can be streamed immediately instead of waiting for every database query. Independent sections load progressively, improving perceived performance and preventing one slow request from blocking the complete page.

#### 10. [Adding Search and Pagination](https://nextjs.org/learn/dashboard-app/adding-search-and-pagination)

I implemented invoice search and pagination with URL search parameters, `useSearchParams`, `usePathname`, and `useRouter`. Search input is debounced, resets pagination, and SQL returns only the matching page of records.

**Next.js improvement:** URL-based state is bookmarkable, shareable, refresh-safe, and compatible with server rendering. Debouncing reduces unnecessary navigation and database requests, while server-side pagination avoids downloading the entire invoice collection.

#### 11. [Mutating Data](https://nextjs.org/learn/dashboard-app/mutating-data)

I created Server Actions for creating, updating, and deleting invoices. Forms submit `FormData` directly, currency values are stored as cents, affected routes are revalidated, and users are redirected after successful changes.

**Next.js optimization:** Server Actions remove the need to build separate mutation API endpoints and keep database operations on the server. `revalidatePath` refreshes only the affected route data so the UI stays consistent without a full application reload.

#### 12. [Handling Errors](https://nextjs.org/learn/dashboard-app/error-handling)

I added database error handling, an invoices error boundary with a retry action, and a custom not-found screen for missing invoice records using `notFound()`.

**Next.js improvement:** route-level error boundaries isolate failures to the relevant part of the application. Users receive a meaningful recovery interface instead of a broken page, while expected missing resources produce a clear `404` experience.

#### 13. [Improving Accessibility](https://nextjs.org/learn/dashboard-app/improving-accessibility)

I used semantic form controls, associated labels, fieldsets and legends, required fields, descriptive image alternative text, and `aria-describedby`, `aria-live`, and `aria-atomic` for validation feedback. Zod validates invoice data on the server.

**Application improvement:** keyboard and assistive-technology users receive understandable controls and live error feedback. Shared server-side validation prevents invalid data from reaching the database and creates a more reliable form experience.

#### 14. [Adding Authentication](https://nextjs.org/learn/dashboard-app/adding-authentication)

I configured Auth.js with a credentials provider, Zod credential validation, bcrypt password comparison, a custom login page, protected dashboard routes, and redirect behavior for authenticated and unauthenticated users.

**Next.js improvement:** authentication runs on the server and route access is checked before protected content is shown. Centralized authorization prevents duplicated checks across every dashboard page and keeps password verification outside the browser.

#### 15. [Adding Metadata](https://nextjs.org/learn/dashboard-app/adding-metadata)

I configured a shared title template, description, metadata base, favicon, Open Graph image, and individual titles for login, dashboard, customers, invoices, create invoice, and edit invoice pages.

**Next.js optimization:** the Metadata API generates the correct document head on the server. Consistent titles, descriptions, icons, and social preview data improve discoverability, browser usability, SEO, and link sharing without manually managing `<head>` tags.

#### 16. [Next Steps](https://nextjs.org/learn/dashboard-app/next-steps)

I completed the full dashboard learning path and consolidated the core skills required to build a modern full-stack Next.js application.

**Development improvement:** the project now has a reusable foundation for future work such as tests, richer customer management, role-based authorization, deployment, monitoring, and further performance measurement.

### Getting started locally

#### Prerequisites

- Node.js 20.9 or later
- npm
- A PostgreSQL database

#### Installation

```bash
git clone https://github.com/antonina-kachusova/Nextjs-Dashboard.git
cd nextjs-dashboard
npm install
```

Create a `.env` file and add your PostgreSQL connection string:

```env
POSTGRES_URL=your_postgresql_connection_string
```

Start the development server:

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Available scripts

```bash
npm run dev    # Start the development server
npm run build  # Create a production build
npm run start  # Start the production server
npm run lint   # Run ESLint
```

### Project status

This is an educational portfolio project based on the official Next.js course. The implementation demonstrates the complete learning path and can be extended with production deployment, automated tests, and additional dashboard features.

## Українська

### Про проєкт

Acme Financial Dashboard — це full-stack застосунок, створений під час проходження офіційного [курсу Next.js App Router](https://nextjs.org/learn/dashboard-app). Він демонструє сучасну фінансову панель з автентифікацією, захищеними маршрутами, аналітикою з бази даних, керуванням рахунками, пошуком, пагінацією, валідацією, обробкою помилок та адаптивним інтерфейсом.

Цей репозиторій показує не лише кінцевий результат, а й покращення продуктивності, користувацького досвіду та процесу розробки, реалізовані протягом усіх 16 розділів курсу.

### Спробуйте застосунок

Щоб отримати доступ до захищеної панелі та переглянути сторінки застосунку, відкрийте сторінку `/login` і введіть тестові дані:

```text
Email: user@nextmail.com
Пароль: 123456
```

Після входу можна переглянути dashboard, клієнтів і рахунки, перевірити пошук та пагінацію, а також створення й редагування рахунків. Після завершення перегляду із застосунку можна вийти.

### Основні можливості

- Адаптивна публічна головна сторінка та захищена панель керування
- Автентифікація за обліковими даними та захист маршрутів
- Огляд доходів, підсумкові картки й останні рахунки
- Отримання даних із PostgreSQL
- Пошук рахунків і пагінація через URL
- Створення, редагування та видалення рахунків
- Серверна валідація форм із доступними повідомленнями про помилки
- Потокове завантаження інтерфейсу зі skeleton-компонентами
- Відновлення після помилок і власна сторінка `404`
- Оптимізовані шрифти, зображення, навігація та metadata

### Технології

- Next.js з App Router
- React і React Server Components
- TypeScript
- Tailwind CSS і CSS Modules
- PostgreSQL та клієнт `postgres`
- Auth.js / NextAuth.js
- Zod
- Heroicons, `clsx` і `use-debounce`

### Що я вивчила — усі 16 розділів курсу

#### 1. [Початок роботи](https://nextjs.org/learn/dashboard-app/getting-started)

Я ознайомилася зі структурою проєкту, папками повторно використовуваних UI-компонентів і утиліт, тестовими даними, TypeScript-типами та локальним процесом розробки.

**Покращення Next.js:** `create-next-app` створює інтегровану основу для production-застосунку з правилами App Router, підтримкою TypeScript, оптимізованими інструментами розробки й Turbopack. Це скорочує початкове налаштування та відразу впорядковує кодову базу.

#### 2. [Стилізація CSS](https://nextjs.org/learn/dashboard-app/css-styling)

Я використала глобальні стилі, utility-класи Tailwind CSS, ізольований CSS Module та `clsx` для умовних стилів статусів рахунків і активних навігаційних посилань.

**Покращення Next.js:** глобальні стилі завантажуються один раз у кореневому layout, CSS Modules запобігають конфліктам назв, а utility-класи дозволяють тримати адаптивне оформлення поруч із компонентом без великої таблиці стилів.

#### 3. [Оптимізація шрифтів і зображень](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images)

Я додала Inter і Lusitana через `next/font`, адаптивні hero-зображення для desktop і mobile та аватари клієнтів через `next/image`.

**Оптимізація Next.js:** шрифти завантажуються під час build і розміщуються разом із застосунком, що усуває додаткові запити браузера та зменшує зміщення layout. Компонент Image резервує розміри зображень, підтримує адаптивну доставку, lazy loading і сучасні формати, покращуючи швидкість та Core Web Vitals.

#### 4. [Створення layout і сторінок](https://nextjs.org/learn/dashboard-app/creating-layouts-and-pages)

Я створила маршрути за файловою системою та спільний dashboard layout із постійною боковою навігацією. Для оглядової сторінки використано route group, який упорядковує код, не змінюючи URL.

**Покращення Next.js:** вкладені layouts зберігають спільний інтерфейс між переходами, уникають зайвих повторних рендерів і прибирають дублювання структури сторінок. Файлова маршрутизація робить зв’язок між URL і кодом зрозумілим.

#### 5. [Навігація між сторінками](https://nextjs.org/learn/dashboard-app/navigating-between-pages)

Я реалізувала навігацію через `next/link` і виділення поточного dashboard-маршруту за допомогою `usePathname` та `clsx`.

**Оптимізація Next.js:** компонент Link забезпечує клієнтські переходи й автоматичне попереднє завантаження маршрутів, коли посилання потрапляють у viewport. Навігація відчувається швидшою, оскільки браузер не перезавантажує всю сторінку.

#### 6. [Налаштування бази даних](https://nextjs.org/learn/dashboard-app/setting-up-your-database)

Я підключила PostgreSQL, визначила таблиці користувачів, клієнтів, рахунків і доходів та створила seed-маршрут із підготовленими тестовими даними.

**Покращення застосунку:** постійні реляційні дані замінили жорстко прописані дані інтерфейсу. Параметризовані SQL-запити формують надійний data layer, а серверне підключення не передає доступ до бази та секретні значення в клієнтський bundle.

#### 7. [Отримання даних](https://nextjs.org/learn/dashboard-app/fetching-data)

Я отримувала дані панелі та рахунків безпосередньо в асинхронних React Server Components. Пов’язані dashboard-запити виконуються паралельно через `Promise.all`, а SQL виконує фільтрацію, joins, сортування, агрегацію та пагінацію поруч із даними.

**Оптимізація Next.js:** Server Components можуть звертатися до бази без окремого клієнтського API-шару й додаткових запитів із браузера. Клієнту надсилається менше JavaScript, чутлива логіка залишається на сервері, а паралельні запити скорочують request waterfalls.

#### 8. [Статичний і динамічний рендеринг](https://nextjs.org/learn/dashboard-app/static-and-dynamic-rendering)

Я навчилася відрізняти контент, який можна підготувати заздалегідь, від даних панелі, залежних від поточного запиту. Захищений dashboard і результати рахунків, керовані URL, формуються відповідно до актуального стану запиту та бази.

**Оптимізація Next.js:** статичний UI можна підготувати й повторно використовувати для швидкості, тоді як динамічний рендеринг зберігає персоналізовані фінансові дані актуальними. Вибір стратегії для кожного маршруту не дозволяє всьому застосунку стати без потреби динамічним.

#### 9. [Streaming](https://nextjs.org/learn/dashboard-app/streaming)

Я додала маршрутний `loading.tsx`, повторно використовувані skeleton-компоненти й окремі Suspense boundaries для карток, доходів, останніх рахунків і таблиці рахунків.

**Оптимізація Next.js:** оболонка сторінки та вже доступний контент можуть надсилатися одразу, не очікуючи завершення всіх запитів до бази. Незалежні секції завантажуються поступово, покращуючи сприйняту швидкість і не дозволяючи одному повільному запиту блокувати всю сторінку.

#### 10. [Додавання пошуку та пагінації](https://nextjs.org/learn/dashboard-app/adding-search-and-pagination)

Я реалізувала пошук і пагінацію рахунків через параметри URL, `useSearchParams`, `usePathname` і `useRouter`. Поле пошуку має debounce, скидає номер сторінки, а SQL повертає лише потрібну сторінку результатів.

**Покращення Next.js:** стан у URL можна зберегти в закладки, поширити посиланням і відновити після оновлення сторінки; він також сумісний із серверним рендерингом. Debounce скорочує зайві переходи й запити до бази, а серверна пагінація не завантажує всю колекцію рахунків.

#### 11. [Зміна даних](https://nextjs.org/learn/dashboard-app/mutating-data)

Я створила Server Actions для додавання, оновлення та видалення рахунків. Форми безпосередньо надсилають `FormData`, суми зберігаються в центах, змінені маршрути ревалідуються, а після успішної операції користувач перенаправляється.

**Оптимізація Next.js:** Server Actions усувають необхідність створювати окремі API endpoints для кожної зміни та залишають операції з базою на сервері. `revalidatePath` оновлює дані лише потрібного маршруту, тому інтерфейс залишається узгодженим без повного перезавантаження застосунку.

#### 12. [Обробка помилок](https://nextjs.org/learn/dashboard-app/error-handling)

Я додала обробку помилок бази даних, invoices error boundary із повторною спробою та власний екран для відсутнього рахунку через `notFound()`.

**Покращення Next.js:** маршрутні error boundaries ізолюють збій у відповідній частині застосунку. Користувач бачить зрозумілий інтерфейс відновлення замість зламаної сторінки, а відсутні ресурси отримують коректний сценарій `404`.

#### 13. [Покращення доступності](https://nextjs.org/learn/dashboard-app/improving-accessibility)

Я використала семантичні елементи форм, пов’язані labels, fieldset і legend, обов’язкові поля, змістовний альтернативний текст зображень та `aria-describedby`, `aria-live` і `aria-atomic` для повідомлень валідації. Zod перевіряє дані рахунків на сервері.

**Покращення застосунку:** користувачі клавіатури й допоміжних технологій отримують зрозумілі елементи керування та живі повідомлення про помилки. Спільна серверна валідація не пропускає некоректні дані до бази та робить роботу з формами надійнішою.

#### 14. [Додавання автентифікації](https://nextjs.org/learn/dashboard-app/adding-authentication)

Я налаштувала Auth.js із credentials provider, Zod-валідацією облікових даних, порівнянням паролів через bcrypt, власною сторінкою входу, захищеними dashboard-маршрутами та перенаправленнями для авторизованих і неавторизованих користувачів.

**Покращення Next.js:** автентифікація виконується на сервері, а доступ перевіряється до показу захищеного контенту. Централізована авторизація не дублює перевірки на кожній dashboard-сторінці та залишає перевірку пароля поза браузером.

#### 15. [Додавання metadata](https://nextjs.org/learn/dashboard-app/adding-metadata)

Я налаштувала спільний шаблон заголовків, опис, metadata base, favicon, Open Graph-зображення й окремі заголовки сторінок login, dashboard, customers, invoices, створення та редагування рахунку.

**Оптимізація Next.js:** Metadata API формує правильний document head на сервері. Узгоджені заголовки, описи, іконки та дані social preview покращують індексацію, зручність вкладок браузера, SEO й поширення посилань без ручного керування тегами `<head>`.

#### 16. [Наступні кроки](https://nextjs.org/learn/dashboard-app/next-steps)

Я завершила повний навчальний шлях зі створення dashboard і закріпила основні навички, необхідні для сучасного full-stack Next.js застосунку.

**Покращення процесу розробки:** проєкт став повторно використовуваною основою для наступних кроків — тестів, розширеного керування клієнтами, рольової авторизації, deployment, monitoring і подальших вимірювань продуктивності.

### Локальний запуск

#### Передумови

- Node.js 20.9 або новіший
- npm
- База даних PostgreSQL

#### Встановлення

```bash
git clone https://github.com/antonina-kachusova/Nextjs-Dashboard.git
cd nextjs-dashboard
npm install
```

Створіть файл `.env` і додайте рядок підключення PostgreSQL:

```env
POSTGRES_URL=your_postgresql_connection_string
```

Запустіть сервер розробки:

```bash
npm run dev
```

Відкрийте [http://localhost:3000](http://localhost:3000) у браузері.

### Доступні команди

```bash
npm run dev    # Запустити сервер розробки
npm run build  # Створити production build
npm run start  # Запустити production-сервер
npm run lint   # Запустити ESLint
```

### Статус проєкту

Це навчальний портфоліо-проєкт на основі офіційного курсу Next.js. Реалізація демонструє повний навчальний шлях і може бути розширена production deployment, автоматизованими тестами та додатковими функціями dashboard.
