# Todo Summary Assistant

A full-stack application that allows users to manage personal to-do items and generate AI-powered summaries that are sent to Slack channels.

## Features

- ✅ **Todo Management**: Create, edit, delete, and mark todos as complete
- 🤖 **AI Summaries**: Generate intelligent summaries of pending tasks using OpenAI
- 💬 **Slack Integration**: Send summaries directly to Slack channels via webhooks
- 📱 **Responsive Design**: Works seamlessly on desktop and mobile devices
- 🎨 **Modern UI**: Built with shadcn/ui components and Tailwind CSS

## Tech Stack

- **Frontend**: React (Next.js 14 with App Router)
- **Backend**: Node.js (Next.js API Routes)
- **Database**: PostgreSQL (Supabase)
- **AI**: OpenAI GPT-4o-mini
- **Notifications**: Slack Incoming Webhooks
- **Styling**: Tailwind CSS + shadcn/ui
- **Deployment**: Vercel

## Prerequisites

- Node.js 18+ 
- A Supabase account and project
- An OpenAI API key
- A Slack workspace with webhook access

## Setup Instructions

### 1. Clone the Repository

\`\`\`bash
git clone <your-repo-url>
cd todo-summary-assistant
npm install
\`\`\`

### 2. Environment Variables

Copy the `.env.example` file to `.env.local` and fill in your values:

\`\`\`bash
cp .env.example .env.local
\`\`\`

Required environment variables:
- `NEXT_PUBLIC_SUPABASE_URL`: Your Supabase project URL
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`: Your Supabase anonymous key
- `SUPABASE_SERVICE_ROLE_KEY`: Your Supabase service role key
- `OPENAI_API_KEY`: Your OpenAI API key
- `SLACK_WEBHOOK_URL`: Your Slack incoming webhook URL

### 3. Database Setup

The application will automatically create the required `todos` table when you first run it. The table schema includes:

- `id` (UUID, Primary Key)
- `title` (Text, Required)
- `description` (Text, Optional)
- `is_completed` (Boolean, Default: false)
- `created_at` (Timestamp)
- `updated_at` (Timestamp)

### 4. Supabase Configuration

1. Create a new project at [supabase.com](https://supabase.com)
2. Go to Settings > API to get your URL and keys
3. The database table will be created automatically via the SQL migration

### 5. OpenAI Setup

1. Create an account at [platform.openai.com](https://platform.openai.com)
2. Generate an API key from the API Keys section
3. Add credits to your account (the app uses GPT-4o-mini which is cost-effective)

### 6. Slack Webhook Setup

1. Go to your Slack workspace
2. Create a new app at [api.slack.com/apps](https://api.slack.com/apps)
3. Enable "Incoming Webhooks" feature
4. Create a new webhook URL for your desired channel
5. Copy the webhook URL to your environment variables

### 7. Run the Application

\`\`\`bash
npm run dev
\`\`\`

Open [http://localhost:3000](http://localhost:3000) in your browser.

## API Endpoints

The application exposes the following REST API endpoints:

- `GET /api/todos` - Fetch all todos
- `POST /api/todos` - Create a new todo
- `PUT /api/todos/:id` - Update a specific todo
- `DELETE /api/todos/:id` - Delete a specific todo
- `POST /api/summarize` - Generate summary and send to Slack

## Usage

1. **Add Todos**: Use the form at the top to create new todos with titles and optional descriptions
2. **Manage Todos**: Check off completed items, edit existing todos, or delete them
3. **Filter Todos**: Use the filter dropdown to view all, pending, or completed todos
4. **Generate Summary**: Click "Send Summary to Slack" to create an AI summary of pending todos and send it to your configured Slack channel

## Architecture Decisions

### Frontend
- **Next.js with App Router**: Provides excellent developer experience with built-in API routes, server components, and optimized performance
- **shadcn/ui**: Modern, accessible component library built on Radix UI primitives
- **Tailwind CSS**: Utility-first CSS framework for rapid UI development

### Backend
- **Next.js API Routes**: Serverless functions that scale automatically and integrate seamlessly with the frontend
- **Supabase**: Managed PostgreSQL with real-time capabilities and excellent developer experience

### AI Integration
- **OpenAI GPT-4o-mini**: Cost-effective model that provides high-quality summaries while keeping costs low
- **Vercel AI SDK**: Streamlined integration with OpenAI and other AI providers

### Communication
- **Slack Webhooks**: Simple, reliable way to send messages to Slack without complex OAuth flows

## Deployment

### Deploy to Vercel

1. Push your code to a GitHub repository
2. Import the repository in [Vercel](https://vercel.com)
3. Configure the environment variables in the Vercel dashboard
4. Deploy

The application will automatically build and deploy. Vercel provides excellent integration with Next.js applications.

### Environment Variables in Production

Make sure to set all required environment variables in your deployment platform:

- Supabase credentials
- OpenAI API key  
- Slack webhook URL

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

MIT License - see LICENSE file for details

## Support

If you encounter any issues:

1. Check that all environment variables are correctly set
2. Verify your Supabase database is accessible
3. Ensure your OpenAI API key has sufficient credits
4. Test your Slack webhook URL independently

For additional help, please open an issue in the GitHub repository.
\`\`\`

```txt file=".env.example"
# Supabase Configuration
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key

# OpenAI Configuration
OPENAI_API_KEY=your_openai_api_key

# Slack Configuration
SLACK_WEBHOOK_URL=your_slack_webhook_url
