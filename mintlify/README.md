# Mintlify Starter Kit

Use the starter kit to get your docs deployed and ready to customize.

Click the green **Use this template** button at the top of this repo to copy the Mintlify starter kit. The starter kit contains examples with

- Guide pages
- Navigation
- Customizations
- API reference pages
- Use of popular components

**[Follow the full quickstart guide](https://starter.mintlify.com/quickstart)**

## Setting up Chat-Bar from @sampleapp.ai/sdk

### Prerequisites

- Node.js version 18.10.0 or higher
- npm package manager
- SampleApp.ai API key
- Mintlify CLI installed

### Installation Steps

1. **Add ChatBar to your Mintlify docs**:

   Create a component in `snippets/chat-bar.jsx`:

   ```jsx
   import React, {useEffect, useRef} from "react";

   export const ChatBar = () => {
     const chatBarRef = useRef(null);

     useEffect(() => {
       // Load the SampleApp SDK
       const script = document.createElement("script");
       script.src =
         "https://cdn.jsdelivr.net/npm/@sampleapp.ai/sdk@latest/dist/index.standalone.umd.js";
       script.onload = () => {
         if (window.SampleAppStandalone && chatBarRef.current) {
           window.SampleAppStandalone.ChatBar(
             {
               placeholder: "Ask me anything...",
               height: "auto",
               playgroundUid: "yourCompanyName",
               typingTexts: [
                 "How do I use yourCompanyName?",
                 "What is yourCompanyName?",
                 "Build with yourCompanyName",
               ],
             },
             chatBarRef.current
           );
         }
       };
       document.head.appendChild(script);

       return () => {
         // Cleanup script on unmount - just remove the script we created
         script.remove();
       };
     }, []);

     return <div ref={chatBarRef} className="w-full"></div>;
   };
   ```

2. **Add to sample-apps.mdx**:

   Create a new page file `sample-apps.mdx` in your docs directory:

   ```mdx
   ---
   title: "Sample Apps"
   description: "Test yourCompanyName in real-time with our interactive playground"
   ---

   import {ChatBar} from "/snippets/chat-bar.jsx";

   # Try Interactive Examples

   Experience yourCompanyName firsthand with our interactive examples below.

   <ChatBar />

   ## What can you build?

   Try asking questions like:

   - "Show me how to integrate yourCompanyName"
   - "What are the main features of yourCompanyName?"
   - "How do I get started with yourCompanyName?"
   ```

3. **Update your docs.json**:
   Add the new page to your navigation by updating `mint.json` or `docs.json`:

   ```json
   {
     "navigation": [
       {
         "group": "Get Started",
         "pages": ["introduction", "quickstart"]
       },
       {
         "group": "Sample Apps",
         "pages": ["sample-apps"]
       }
     ]
   }
   ```

### Testing the Integration

1. **Start the development server**:

   ```bash
   mint dev
   ```

2. **Verify the chat functionality**:
   - Open your browser to `http://localhost:3000`
   - Look for the chat interface
   - Test sending and receiving messages

## Development

Install the [Mintlify CLI](https://www.npmjs.com/package/mint) to preview your documentation changes locally. To install, use the following command:

```
npm i -g mint
```

Run the following command at the root of your documentation, where your `docs.json` is located:

```
mint dev
```

View your local preview at `http://localhost:3000`.

## Publishing changes

Install our GitHub app from your [dashboard](https://dashboard.mintlify.com/settings/organization/github-app) to propagate changes from your repo to your deployment. Changes are deployed to production automatically after pushing to the default branch.

## Need help?

### Troubleshooting

- If your dev environment isn't running: Run `mint update` to ensure you have the most recent version of the CLI.
- If a page loads as a 404: Make sure you are running in a folder with a valid `docs.json`.
- **Chat not appearing**: Check that your API key is correctly set in the environment variables
- **Build errors**: Ensure the SDK is properly installed and imported
- **Styling issues**: Verify the theme matches your Mintlify configuration

### Resources

- [Mintlify documentation](https://mintlify.com/docs)
- [Mintlify community](https://mintlify.com/community)
- [SampleApp.ai Discord Support](https://discord.gg/GFwngrJ5pS)
