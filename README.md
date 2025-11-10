# Next.js Image Generation App with n8n Integration

A full-featured Next.js application for uploading images, writing prompts, and generating AI images via n8n webhook integration.

## Features

- **Drag & Drop Image Upload** - Easy image selection with preview
- **Prompt Input** - Write custom prompts for image generation
- **n8n Webhook Integration** - Send requests to your n8n workflow
- **Client Personalization** - Support for multiple brands/clients
- **Local History** - Store last 12 generations per client
- **Credit Management** - Handle insufficient credits gracefully
- **Responsive Design** - Works on desktop and mobile
- **TypeScript** - Type-safe codebase
- **Tailwind CSS** - Modern styling

## Quick Setup

### 1. Clone and Install

```bash
git clone https://github.com/Se7en198/nextjs-image-generation-app.git
cd nextjs-image-generation-app
npm install
```

### 2. Create .env.local

Copy `.env.example` to `.env.local` and fill in your values:

```bash
cp .env.example .env.local
```

Then edit `.env.local`:

```
NEXT_PUBLIC_N8N_WEBHOOK_URL=https://your-n8n-instance.com/webhook/your-webhook-id
NEXT_PUBLIC_MAX_MB=10
NEXT_PUBLIC_ALLOWED_TYPES=image/jpeg,image/png
```

### 3. Run Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### 4. Build for Production

```bash
npm run build
npm start
```

## Project Structure

```
.
├── app/
│   ├── page.tsx                 # Main page
│   └── api/
│       └── health/
│           └── route.ts         # Health check endpoint
├── components/
│   ├── UploadDropzone.tsx       # Image upload component
│   ├── HistoryGrid.tsx          # History grid display
│   └── BrandHeader.tsx          # Brand header
├── lib/
│   ├── n8n.ts                   # n8n webhook helper
│   └── brands.ts                # Brand configuration
├── public/
│   └── brands/                  # Brand logos
├── package.json
├── tsconfig.json
├── next.config.js
└── tailwind.config.js
```

## Environment Variables

- `NEXT_PUBLIC_N8N_WEBHOOK_URL` - Your n8n webhook URL
- `NEXT_PUBLIC_MAX_MB` - Maximum file size in MB
- `NEXT_PUBLIC_ALLOWED_TYPES` - Allowed MIME types

## Deployment

### Vercel (Recommended)

1. Push code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Click "New Project" and select your repository
4. Add environment variables
5. Click "Deploy"

## API Integration

The app sends POST requests to your n8n webhook with:

```json
{
  "image": File,
  "prompt": "string",
  "customerId": "string"
}
```

Expected response:

```json
{
  "imageUrl": "https://...",
  "success": true
}
```

## Support for Error Codes

- **402** - Insufficient credits
- **4xx/5xx** - Server errors

## Tech Stack

- Next.js 15+
- React 18+
- TypeScript
- Tailwind CSS
- react-dropzone

## License

MIT
