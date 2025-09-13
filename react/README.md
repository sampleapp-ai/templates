# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

## Setting up Chat-Bar from @sampleapp.ai/sdk

### Prerequisites

- Node.js version 18.10.0 or higher
- npm, yarn, pnpm, or bun package manager
- SampleApp.ai API key

### Installation Steps

1. **Install the SDK package**:

   ```bash
   npm install @sampleapp.ai/sdk
   # or
   yarn add @sampleapp.ai/sdk
   # or
   pnpm add @sampleapp.ai/sdk
   # or
   bun add @sampleapp.ai/sdk
   ```

2. **Create a ChatBar component**:

   Create `src/components/ChatBar.tsx`:

   ```tsx
   import {ChatBar} from "@sampleapp.ai/sdk";

   export default function CustomChatBar() {
     return (
       <ChatBar
         playgroundUid="yourCompanyName" // fill in your company name
         theme="light" // or "dark" to match your site theme
         height="auto"
         typingTexts={[
           "How can I help you with the documentation?",
           "Ask me about this project",
           "What would you like to know?",
         ]}
       />
     );
   }
   ```

3. **Integrate into your app**:

   Add the ChatBar to your main App component in `src/App.tsx`:

   ```tsx
   import "./App.css";
   import CustomChatBar from "./components/ChatBar";

   function App() {
     return (
       <div>
         <CustomChatBar />
       </div>
     );
   }

   export default App;
   ```

### Testing the Integration

1. **Start the development server**:

   ```bash
   npm run dev
   # or
   yarn dev
   # or
   pnpm dev
   # or
   bun dev
   ```

2. **Verify the chat functionality**:
   - Open your browser to `http://localhost:5173` (default Vite port)
   - Look for the chat interface
   - Test sending and receiving messages

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default tseslint.config([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      ...tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      ...tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      ...tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from "eslint-plugin-react-x";
import reactDom from "eslint-plugin-react-dom";

export default tseslint.config([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs["recommended-typescript"],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

## Troubleshooting

- **Chat not appearing**: Check that your API key is correctly set in the environment variables (use `VITE_` prefix for Vite)
- **Build errors**: Ensure the SDK is properly installed and imported
- **Styling issues**: Verify the theme matches your app configuration
- **Environment variables not loading**: Make sure the `.env` file is in the root directory and variables start with `VITE_`

For more help, refer to the [SampleApp.ai Documentation](https://sampleapp.ai/docs).
