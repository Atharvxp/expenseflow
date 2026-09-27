# ExpenseFlow

A modern full-stack personal expense tracker built with **React, Vite, Supabase, and Vercel**.

ExpenseFlow helps users track income and expenses, manage monthly budgets, view spending reports, and manage their profile and app preferences through a clean responsive interface.

## Live Demo

**https://expenseflow1.vercel.app**

## Features

- 🔐 Supabase email/password authentication
- 💰 Income and expense tracking
- ✏️ Add, edit, and delete transactions
- 🔎 Transaction search and filtering
- 📊 Spending reports and category breakdowns
- 🎯 Monthly category budgets with progress tracking
- ⚠️ Over-budget indicators
- 🌙 Light and dark themes
- ⚙️ Profile, currency, and preference settings
- 🔒 Row Level Security (RLS) for user-specific data
- 📱 Responsive React UI
- 🚀 Production deployment on Vercel

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React |
| Build Tool | Vite |
| Styling | CSS / Tailwind-style utility patterns |
| Charts | Recharts |
| Backend | Supabase |
| Database | PostgreSQL |
| Authentication | Supabase Auth |
| Security | Supabase Row Level Security |
| Hosting | Vercel |

## Architecture

```text
React + Vite
     │
     ├── Authentication ──────► Supabase Auth
     │
     ├── Transactions ─────────► PostgreSQL
     │
     ├── Budgets ──────────────► PostgreSQL
     │
     └── Profiles / Settings ──► PostgreSQL

Supabase RLS
     │
     └── Users can access only their own data

Vercel
     │
     └── Production deployment
```

## Database

ExpenseFlow uses three main tables:

- `profiles` — user profile and preferences
- `transactions` — income and expense records
- `budgets` — monthly category budgets

All user-owned data is protected using **Supabase Row Level Security (RLS)**.

## Local Development

### 1. Clone the repository

```bash
git clone https://github.com/Atharvxp/expense-tracker.git
cd expense-tracker
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create `.env.local`:

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
```

Never commit `.env.local` or any Supabase service-role key.

### 4. Start the development server

```bash
npm run dev
```

The app will normally be available at:

```text
http://localhost:5173
```

## Production

The application is deployed through Vercel and connected to the GitHub repository.

Pushing to the `main` branch triggers a new production deployment.

## Security

ExpenseFlow is designed around Supabase's client-side authentication and database security model:

- Authentication is handled by Supabase Auth.
- User-owned rows contain a `user_id`.
- RLS policies restrict records to the authenticated user.
- The Supabase publishable key is safe to use in the browser when RLS is correctly configured.
- Supabase service-role credentials are never exposed to the frontend.

## Future Improvements

Potential V2 improvements include:

- Transaction ingestion through an approved banking / Account Aggregator provider
- Pending transaction approval workflow
- Automatic transaction categorization suggestions
- Payment-type detection
- CSV import/export
- Recurring transactions
- Advanced analytics
- Performance-oriented code splitting
- Custom domain

> Direct arbitrary UPI-app transaction access is not assumed. Any future financial-data integration should use an approved provider/API and explicit user authorization.

## Project Structure

```text
src/
├── auth/
│   ├── AuthContext.jsx
│   └── ProtectedRoute.jsx
├── components/
│   └── TransactionModal.jsx
├── context/
│   └── AppContext.jsx
├── layout/
│   └── AppLayout.jsx
├── pages/
│   ├── Dashboard.jsx
│   ├── Transactions.jsx
│   ├── Reports.jsx
│   ├── Budgets.jsx
│   ├── Settings.jsx
│   ├── Login.jsx
│   └── Signup.jsx
├── lib/
│   └── supabase.js
├── App.jsx
├── index.css
└── main.jsx
```

## License

This project is intended as a portfolio and learning project.
