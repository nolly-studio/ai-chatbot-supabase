<a href="https://chat.vercel.ai/">
  <img alt="Next.js 14 and App Router-ready AI chatbot." src="app/(chat)/opengraph-image.png">
  <h1 align="center">Next.js AI Chatbot x Supabase</h1>
</a>

<p align="center">
  An Open-Source AI Chatbot Template Built With Next.js and the AI SDK by Vercel.
</p>

<p align="center">
  <a href="#features"><strong>Features</strong></a> ·
  <a href="#model-providers"><strong>Model Providers</strong></a> ·
  <a href="#deploy-your-own"><strong>Deploy Your Own</strong></a> ·
  <a href="#running-locally"><strong>Running locally</strong></a>
</p>
<br/>

## Features

- [Next.js](https://nextjs.org) App Router
  - Advanced routing for seamless navigation and performance
  - React Server Components (RSCs) and Server Actions for server-side rendering and increased performance
  - Built-in optimizations for images, fonts, and static assets
- [AI SDK](https://sdk.vercel.ai/docs)
  - Unified API for generating text, structured objects, and tool calls with LLMs
  - Hooks for building dynamic chat and generative user interfaces
  - Supports OpenAI (default), Anthropic, Cohere, and other model providers
  - Built-in streaming support for real-time AI responses
- [shadcn/ui](https://ui.shadcn.com)
  - Styling with [Tailwind CSS](https://tailwindcss.com)
  - Component primitives from [Radix UI](https://radix-ui.com) for accessibility and flexibility
  - Customizable themes and dark mode support
- [Supabase](https://supabase.com) Integration
  - [Supabase Postgres DB](https://supabase.com/docs/guides/database) for robust chat history and user data storage
  - [Supabase File Storage](https://supabase.com/docs/guides/storage) for efficient file management and uploads
  - [Supabase Auth](https://supabase.com/docs/guides/auth) with multiple authentication providers and row-level security
  - Real-time subscriptions for live updates

## Model Providers

This template ships with OpenAI `gpt-4o` as the default. However, with the [AI SDK](https://sdk.vercel.ai/docs), you can switch LLM providers to [OpenAI](https://openai.com), [Anthropic](https://anthropic.com), [Cohere](https://cohere.com/), and [many more](https://sdk.vercel.ai/providers/ai-sdk-providers) with just a few lines of code.

<div id="youtube-onboarding-video">

<div align="left">
  <h2>YouTube Onboarding Video</h2>
   <h4>This video walks you through how to set up the ai chatbot with supabase from scratch. We will:</h4>
  <ul style="text-align: left; display: inline-block;">
    <li>Setup a new Supabase project using the CLI</li>
    <li>Link it to our app</li>
    <li>Setup environment variables</li>
    <li>Run the DB migrations to configure the schema</li>
  </ul>
  <a href="https://youtu.be/YMEyNXP59Ss">
    <img src="https://github.com/nolly-studio/ai-chatbot-supabase/blob/main/readme-video-thumbnail.png" width="85%" alt="YouTube Onboarding Video" />
  </a>
</div>

</div>


## Getting Started

### Quick Start Video Guide

Watch our comprehensive onboarding video to quickly set up your development environment and understand the project structure: [Watch Tutorial](#)

### Prerequisites

Before you begin, ensure you have the following installed:

- Node.js 18+
- pnpm (`npm install -g pnpm`)
- Git
- A code editor (we recommend VS Code)

### Supabase Setup

1. **Install the Supabase CLI**
   Choose the installation method for your operating system:

   - Mac:
     ```bash
     brew install supabase/tap/supabase
     ```
   - Windows (PowerShell):
     ```powershell
     scoop bucket add supabase https://github.com/supabase/scoop-bucket.git
     scoop install supabase
     ```
   - Linux:
     ```bash
     brew install supabase/tap/supabase
     ```
   - NPM/Bun:
     ```bash
     npx supabase <command>
     ```

2. **Create a Supabase Project**

   ```bash
   # Create a new project
   npx supabase projects create -i "ai-chatbot-supabase"

   # Note: Save the project ID and database password shown after creation
   ```

   > Your Organization ID can be found in the Supabase Dashboard URL after selecting an organization

3. **Link Your Project**

   ```bash
   # Initialize Supabase configuration
   npx supabase init

   # Link to your remote project
   npx supabase link --project-ref your-project-id
   ```

   You'll need your project ID and database password from step 2.

4. **Configure Environment Variables**
   Create a `.env.local` file with the following variables:

   ```bash
   NEXT_PUBLIC_SUPABASE_URL=<api-url>
   NEXT_PUBLIC_SUPABASE_ANON_KEY=<anon-key>
   ```

   > Find these values in your Supabase project dashboard under Project Settings > API

5. **Initialize Database Schema**

   ```bash
   # Apply all migrations
   supabase db push

   # Verify the schema
   supabase db reset --dry-run
   ```

### Local Development

1. **Clone and Install**

   ```bash
   git clone https://github.com/your-username/ai-chatbot-supabase.git
   cd ai-chatbot-supabase
   pnpm install
   ```

2. **Start Development Server**

   ```bash
   pnpm dev
   ```

   The application will be available at [http://localhost:3000](http://localhost:3000)

3. **Development Commands**
   ```bash
   pnpm build          # Build for production
   pnpm start          # Start production server
   pnpm lint          # Run ESLint
   pnpm type-check    # Run TypeScript checks
   ```

### Troubleshooting

Common issues and solutions:

- **Supabase Connection Issues**

  - Verify your environment variables are correctly set
  - Check if the database is active in Supabase dashboard

- **Build Errors**
  - Clear `.next` folder: `rm -rf .next`
  - Clean install dependencies: `pnpm clean-install`

For more help, open an issue.

## Deploy with Vercel

### Prerequisites

- A [Vercel account](https://vercel.com/signup)
- A [Supabase account](https://supabase.com/dashboard/sign-in)
- An [OpenAI API key](https://platform.openai.com/api-keys)

### Deployment Steps

1. **Fork the Repository**

   ```bash
   https://github.com/your-username/ai-chatbot-supabase
   ```

2. **Configure Vercel Project**

   - Go to [Vercel Dashboard](https://vercel.com/dashboard)
   - Click "New Project"
   - Import your forked repository
   - Select "Next.js" as the framework

3. **Set Environment Variables**
   In your Vercel project settings, add the following environment variables:

```bash
# Required
NEXT_PUBLIC_SUPABASE_URL=           # From Supabase project settings
NEXT_PUBLIC_SUPABASE_ANON_KEY=      # From Supabase project settings
OPENAI_API_KEY=                     # Your OpenAI API key
```

4. **Configure Build Settings**
   In your Vercel project settings:

   - Build Command: `pnpm build`
   - Output Directory: `.next`
   - Install Command: `pnpm install`

5. **Deploy**
   - Click "Deploy"
   - Vercel will automatically build and deploy your application

