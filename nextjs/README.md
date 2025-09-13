This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

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
   "use client";

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

3. **Add it to a page**:

   Add to specific pages\*\*:

   You can also add the ChatBar to specific pages by importing it in `src/app/page.tsx`:

   ```tsx
   import Image from "next/image";
   import CustomChatBar from "../components/ChatBar";

   export default function Home() {
     return (
       <div>
         <CustomChatBar />
       </div>
     );
   }
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
   - Open your browser to `http://localhost:3000`
   - Look for the chat interface
   - Test sending and receiving messages

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.

## Troubleshooting

- **Chat not appearing**: Check that your API key is correctly set in the environment variables (use `NEXT_PUBLIC_` prefix for client-side access)
- **Build errors**: Ensure the SDK is properly installed and imported
- **Styling issues**: Verify the theme matches your Next.js configuration
- **Hydration errors**: Make sure the ChatBar component is marked with `'use client'` directive

For more help, refer to the [SampleApp.ai Documentation](https://sampleapp.ai/docs).
