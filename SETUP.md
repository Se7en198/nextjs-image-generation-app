# Setup Instructions - Next.js Image Generation App

## Fast Local Setup with Script

Sigue estos pasos para clonar el repositorio y generar todos los archivos automáticamente:

### Paso 1: Clonar el repositorio

```bash
git clone https://github.com/Se7en198/nextjs-image-generation-app.git
cd nextjs-image-generation-app
```

### Paso 2: Copiar las instrucciones de abajo y ejecutar en tu terminal

Abre una terminal en la carpeta del proyecto y copia-pega TODO el siguiente bloque:

```bash
# Crear estructura de carpetas
mkdir -p app/api/health lib components public/brands

# Crear tsconfig.json
cat > tsconfig.json << 'EOF'
{"compilerOptions": {"lib": ["dom", "dom.iterable", "esnext"], "allowJs": true, "skipLibCheck": true, "strict": true, "noEmit": true, "esModuleInterop": true, "module": "esnext", "moduleResolution": "bundler", "resolveJsonModule": true, "isolatedModules": true, "jsx": "preserve", "incremental": true, "paths": {"@/*": ["./*"]}, "plugins": [{"name": "next"}]}, "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"], "exclude": ["node_modules"]}
EOF

# Crear next.config.js
cat > next.config.js << 'EOF'
/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
}

module.exports = nextConfig
EOF

# Crear tailwind.config.js
cat > tailwind.config.js << 'EOF'
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    './app/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
EOF

# Crear postcss.config.js
cat > postcss.config.js << 'EOF'
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
EOF

# Crear .env.local (reemplaza con tu URL real de n8n)
cat > .env.local << 'EOF'
NEXT_PUBLIC_N8N_WEBHOOK_URL=https://your-n8n-instance.com/webhook/your-webhook-id
NEXT_PUBLIC_MAX_MB=10
NEXT_PUBLIC_ALLOWED_TYPES=image/jpeg,image/png
EOF
```

### Paso 3: Copiar los archivos de código fuente

Tiene que copiar estos archivos desde el CHAT IA:
- app/page.tsx
- app/api/health/route.ts
- lib/n8n.ts
- lib/brands.ts
- components/UploadDropzone.tsx
- components/HistoryGrid.tsx
- components/BrandHeader.tsx

O usa este script para crear archivos vacíos como placeholder:

```bash
touch app/page.tsx
touch app/api/health/route.ts
touch lib/n8n.ts
touch lib/brands.ts
touch components/UploadDropzone.tsx
touch components/HistoryGrid.tsx
touch components/BrandHeader.tsx
```

### Paso 4: Instalar dependencias

```bash
npm install
```

### Paso 5: Actualizar .env.local

Abre `.env.local` y actualiza `NEXT_PUBLIC_N8N_WEBHOOK_URL` con tu URL real de n8n webhook.

### Paso 6: Agregar el código desde el chat IA

Copia el código de cada archivo desde el tab del CHAT IA y pégalo en los archivos correspondientes.

### Paso 7: Ejecutar localmente

```bash
npm run dev
```

Abre http://localhost:3000 en tu navegador.

### Paso 8: Verificar que funciona

1. Prueba subiendo una imagen
2. Escribe un prompt
3. Haz clic en "Generate Image"

### Paso 9: Commit y Push a GitHub

```bash
git add .
git commit -m "Add complete source code and configuration files"
git push origin main
```

### Paso 10: Deploy en Vercel

1. Ve a https://vercel.com/dashboard
2. Haz clic en "New Project"
3. Conecta el repositorio de GitHub
4. Vercel detectará Next.js automáticamente
5. Agrega las variables de entorno:
   - NEXT_PUBLIC_N8N_WEBHOOK_URL
   - NEXT_PUBLIC_MAX_MB
   - NEXT_PUBLIC_ALLOWED_TYPES
6. Haz clic en "Deploy"

## ¿Problemas?

- **npm install falla**: Asegúrate de tener Node.js 18+ instalado
- **Comando no encontrado**: Usa `bash` o `zsh` según tu terminal
- **Archivos no se crean**: Intenta crear las carpetas manualmente primero
