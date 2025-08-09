# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.

Online Guitar Shop
A 3-page React + Apollo Client app that fetches guitar brands, models, and details from a GraphQL API. It includes internationalization (English and Albanian), loading/error states, and a responsive UI built with styled-components.

What’s included


Page 1: Guitar Brands (compact, responsive grid)

Page 2: Guitar Models (search, filter by type, optional sorting)

Page 3: Guitar Details (Specs and Musicians tabs)

Apollo Client for data fetching

Language support (English and Albanian)

Loading and error handling components

Clean, responsive UI built with styled-components

Albanian translations for UI and guitar descriptions

Prerequisites


Node.js 14+ (LTS)

npm or yarn

Repo structure (typical)


apollo/

client.js

queries.js



contexts/

LanguageContext.jsx



components/

BrandCard.jsx

ModelCard.jsx

ErrorMessage.jsx

LoadingSpinner.jsx

SearchFilter.jsx

Layout.jsx



pages/

BrandsPage.jsx

ModelsPage.jsx

GuitarDetailsPage.jsx



App.jsx

main.jsx

styles/

global.css



Setup and installation


Clone the repo

git clone 

cd your-repo-name



Install dependencies

npm install

or yarn



Run the app

npm run dev

or yarn dev
The exact script may vary depending on your setup. If you use CRA, try npm start. If you use Vite, npm run dev is typical.



Configuration


GraphQL endpoint used by the app:

https://graphql-api-brown.vercel.app/api/graphql



If you need to override the endpoint, edit src/apollo/client.js and change the uri (or set up an environment variable if you extend the project).

Testing the GraphQL API (sanity checks)


Open GraphQL Playground (in-browser) at:

https://graphql-api-brown.vercel.app/api/graphql



Example queries to test:

Simple type:

query { __typename }



List brands (adjust field names to match the current schema):

query { findAllBrands { id name origin image } }





Localization and translating guitar descriptions


The app includes English and Albanian translations via LanguageContext.jsx.

To translate guitar descriptions, a translateDescription helper is wired into the context. Extend the guitarDescriptions maps to cover new guitars as you add more data.

When viewing a guitar on Page 3, the description uses translateDescription to show the Albanian (or English) version if available.

Usage notes


Page 1 (Brands): Compact brand tiles; click a brand to go to Page 2

Page 2 (Models): Search by name, filter by guitar type, and sort by name/price/type (enum-based sort values depend on your API)

Page 3 (Guitar Details): Tabs for Specs and Musicians; shows 2 musicians at a time with pagination dots

Language switcher in the footer to toggle between English and Albanian

GraphQL tips (quick)


If you see 400 errors, verify the query matches the API schema and input types

Use GraphQL Playground to test with real IDs (brandId and modelId)

If you see null data, check route params and IDs passed from the UI

Testing locally (step-by-step)


Start the app (in the project folder)

npm run dev

or yarn dev



Open in the browser

http://localhost:5173 (port may vary)



Navigate through the app

Page 1: Brands – click a brand to go to Page 2

Page 2: Models – use search and type filter; click a model to go to Page 3

Page 3: Guitar Details – view Specs and Musicians tabs



Use the language switcher in the footer to toggle between English and Albanian

Troubleshooting


400 Bad Request on GraphQL:

Test exact queries in GraphQL Playground with real IDs

Confirm sortBy and other inputs match the API (enum values, input object shapes)



Data missing or IDs not found:

Verify IDs by inspecting the data from findAllBrands and findBrandModels

Ensure route params are passed correctly (brandId and id) to GuitarDetailsPage



Localization notes


The app includes English and Albanian translations for UI and guitar descriptions (where provided)

Extend guitarDescriptions maps to cover additional guitars as you add data