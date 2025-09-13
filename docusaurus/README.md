# Website

This website is built using [Docusaurus](https://docusaurus.io/), a modern static website generator.

## Installation

```bash
yarn
```

## Setting up Chat-Bar from @sampleapp.ai/sdk

### Prerequisites

- Node.js version 18.10.0 or higher
- Yarn package manager
- SampleApp.ai API key

### Installation Steps

1. **Install the SDK package**:

   ```bash
   yarn add @sampleapp.ai/sdk
   ```

2. **Add ChatBar to your Docusaurus site**:

   Create a custom component in `src/components/ChatBar.tsx`:

   ```tsx
   import React from "react";
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

3. **Integrate into your layout**:

   Add the ChatBar to your `src/pages/index.tsx` or create a custom layout:

   ```tsx
   import React from "react";
   import Layout from "@theme/Layout";
   import CustomChatBar from "../components/ChatBar";

   export default function Home() {
     return (
       <Layout>
         {/* Your existing content */}
         <CustomChatBar />
       </Layout>
     );
   }
   ```

### Testing the Integration

1. **Start the development server**:

   ```bash
   yarn start
   ```

2. **Verify the chat functionality**:
   - Open your browser to `http://localhost:3000`
   - Look for the chat interface
   - Test sending and receiving messages

## Local Development

```bash
yarn start
```

This command starts a local development server and opens up a browser window. Most changes are reflected live without having to restart the server.

## Build

```bash
yarn build
```

This command generates static content into the `build` directory and can be served using any static contents hosting service.

## Deployment

Using SSH:

```bash
USE_SSH=true yarn deploy
```

Not using SSH:

```bash
GIT_USER=<Your GitHub username> yarn deploy
```

If you are using GitHub pages for hosting, this command is a convenient way to build the website and push to the `gh-pages` branch.

## Troubleshooting

- **Chat not appearing**: Check that your API key is correctly set in the environment variables
- **Build errors**: Ensure the SDK is properly installed and imported
- **Styling issues**: Verify the theme matches your Docusaurus configuration

For more help, refer to the [SampleApp.ai Discord Support](https://discord.gg/GFwngrJ5pS).
