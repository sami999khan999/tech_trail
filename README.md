<div align="center">

# Tech Trail

**A small electronics store front end: product catalogue and shopping cart with React, Redux Toolkit and Tailwind CSS.**

![React](https://img.shields.io/badge/React-18.2-61DAFB?logo=react&logoColor=black)
![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-1.9-764ABC?logo=redux&logoColor=white)
![React Router](https://img.shields.io/badge/React_Router-6-CA4245?logo=reactrouter&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.3-06B6D4?logo=tailwindcss&logoColor=white)
![Create React App](https://img.shields.io/badge/Create_React_App-5-09D3AC?logo=createreactapp&logoColor=white)

</div>

---

## About

Tech Trail is a single-page e-commerce demo for gadgets (cameras, TVs, headphones, consoles, smart
watches). Products are fetched from a remote JSON API with a Redux Toolkit async thunk, and the cart
lives in a Redux slice that is saved to `localStorage`, so it survives a page reload. It was built
to practise Redux Toolkit, React Router and Tailwind CSS together.

## Features

- **Hero slider** — five full-width slides with a headline, text and call-to-action, previous / next
  buttons.
- **Product grid** — cards with image, category, name, description, price (formatted as USD) and an
  "Add to cart" button; loading and error status while products are fetched.
- **Cart** — add, increase / decrease quantity, remove an item, clear the cart, per-line totals and a
  subtotal; the navbar shows the number of items.
- **Toasts** — `react-hot-toast` messages for every cart action.
- **Persistence** — cart contents kept in `localStorage`.
- **Routes** — `/` (slider + products), `/products`, `/products/:id`, `/cart` and a catch-all
  not-found page.

## Tech stack

| Layer | Technology |
|---|---|
| UI | React 18 (Create React App 5) |
| State | Redux Toolkit 1.9 (`createSlice`, `createAsyncThunk`), React Redux |
| Routing | React Router 6 |
| Data | Axios, remote products API |
| Styling | Tailwind CSS 3.3 |
| Extras | `react-hot-toast`, `react-icons` |

## Project structure

```text
src/
├── App.js                        # layout and routes
├── index.js                      # Redux Provider + BrowserRouter
├── app/store.js                  # store; dispatches the product fetch on start
├── features/products/
│   ├── porductSlice.js           # products: fetch thunk, loading / error status
│   └── cartSlice.js              # cart: add, decrease, remove, clear, subtotal, localStorage
├── components/                   # Navbar, Footer, Slider, Slide, Card
├── pages/                        # Home, Products, Cart, NotFound
└── utilities/currencyFormatter.js
build/                            # a committed production build
```

## Getting started

**Prerequisites:** Node.js and npm.

```bash
git clone https://github.com/sami999khan999/tech_trail.git
cd tech_trail
npm install
npm start          # http://localhost:3000
```

| Script | What it does |
|---|---|
| `npm start` | development server |
| `npm run build` | production build into `build/` |
| `npm test` | Jest test runner (no tests are written yet) |

No environment variables are needed: the products URL is set in
`src/features/products/porductSlice.js`.

## Status

Practice project. Products come from a hosted Glitch API that may no longer respond, in which case
the grid shows "Something went wrong!". The slide buttons link to `/products/<category>`, which
shows the full list (there is no category filter), and "Checkout" returns to the home page.
