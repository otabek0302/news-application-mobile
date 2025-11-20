# News App (Expo / React Native)

A cross-platform React Native news application built with Expo and TypeScript. Uses file-based routing from expo-router and fetches news from an external News API. Clean architecture with components, services, and custom hooks for maintainability.

---

## Features

- Fetch and display latest news articles
- Category filtering (e.g., Technology, Sports, Business)
- Article detail screen with full content and webview
- Smooth navigation using expo-router / React Navigation
- TypeScript + strict typing
- Works on Android, iOS, and web (Expo)

---

## Tech stack

- Expo (managed workflow) — see app.json
- React Native
- TypeScript
- expo-router
- Axios / Apisauce (HTTP client)
- react-native-webview
- react-native-gesture-handler, reanimated, safe-area-context, etc.

Key files:
- package.json — project scripts & dependencies
- tsconfig.json — TypeScript config (extends expo/tsconfig.base)
- app/ — entry and routes (expo-router)
- services/GlobalApi.ts — API helper/service
- constants/Colors.ts — color constants
- components/ — UI components
- assets/ — images & fonts
- eas.json — EAS build configuration

---

## Prerequisites

- Node.js (recommended LTS)
- npm (or yarn / pnpm)
- Expo CLI or use `npx expo` directly
- For native builds: Xcode (macOS) or Android Studio
- (Optional) EAS CLI for production builds

---

## Quick start (development)

1. Clone
   git clone https://github.com/otabek0302/news-application-mobile.git
   cd news-application-mobile

2. Install
   npm install

3. Start Metro / Dev server
   npm start
   or
   npx expo start

4. Run
   - Android emulator / device: npx expo run:android or open from Expo Dev Tools
   - iOS simulator: npx expo run:ios (macOS) or use Expo Dev Tools to open simulator
   - Expo Go: scan QR code from the dev tools

Notes:
- This project uses expo-router file-based routing — edit files in the app/ directory to add pages/routes.

---

## Scripts (from package.json)

- start: expo start
- android: expo start --android
- ios: expo start --ios
- web: expo start --web
- test: jest --watchAll
- lint: expo lint
- reset-project: node ./scripts/reset-project.js

Run scripts with npm, or prefix with npx when necessary:
npm run start

---

## Environment / API key

This app fetches news from an external News API (e.g., NewsAPI.org). Add your API key before running:

Option A — Edit service file
- Open services/GlobalApi.ts (or the relevant API file in services/) and replace the placeholder API key with your key, or provide a configuration constant.

Example (pseudo):
const API_KEY = 'YOUR_API_KEY';
export const BASE_URL = `https://newsapi.org/v2/...&apiKey=${API_KEY}`;

Option B — Use environment variables (recommended)
1. Create a .env file at the project root:
   EXPO_PUBLIC_NEWS_API_KEY=your_api_key_here

2. Read it at runtime:
- For Expo-managed apps you can use expo-constants or the built-in Expo config to surface public env values, or use expo-config-plugins.
- Example using process.env (with appropriate bundler setup) or using a library like react-native-dotenv.

Make sure you never commit secret keys to git. For EAS builds, configure secrets via EAS.

---

## EAS (Expo Application Services)

This project contains eas.json with configured build profiles (development, preview, production). Example uses an EAS projectId in app.json and eas.json. To build using EAS CLI:

1. Install and login:
   npm install -g eas-cli
   eas login

2. Configure credentials (once) and run:
   eas build --platform android --profile production
   eas build --platform ios --profile production

For internal/dev builds use the development or preview profiles defined in eas.json.

---

## Project structure (top-level / important files)

- .gitignore
- README.md
- package.json
- package-lock.json
- tsconfig.json
- app.json
- eas.json
- app/
  - +not-found.tsx
  - _layout.tsx
  - index.tsx
  - news/ (route folder)
- components/
  - home/ (home-related components)
- services/
  - GlobalApi.ts
- constants/
  - Colors.ts
- assets/
  - fonts/
  - images/
    - icon.png, adaptive-icon.png, splash-icon.png, favicon.png (referenced by app.json)
- scripts/
  - reset-project.js (provided by create-expo-app starter)

(Adjust the tree as you add more screens, hooks, and components.)

---

## Notes about routing & entry

- The app uses expo-router for file-based routing. The app entry is configured via "main": "expo-router/entry" in package.json.
- Edit and add screens inside the app/ directory to create routes automatically.

---

## Testing & Linting

- Tests: jest with jest-expo preset (script: npm run test)
- Lint: expo lint (script: npm run lint)

---

## Contributing

Contributions are welcome. Suggested workflow:
1. Fork the repository
2. Create a new branch: git checkout -b feature/your-feature
3. Commit changes: git commit -m "Add: description"
4. Push: git push origin feature/your-feature
5. Open a Pull Request to the main branch

Include meaningful commit messages and, where appropriate, tests.

---

## Contact

For questions or feedback:
- otabekjon0302@gmail.com
- otabekjon2002@mail.ru

---

If you want, I can:
- Create a ready-to-commit README.md file using the exact content above,
- Or customize it with your preferred package manager (yarn / pnpm), CI badges, or additional developer instructions (how to wire the API key into the existing services/GlobalApi.ts). Which would you prefer?
