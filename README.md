# AI Architecture Playground — Deploy en Vercel

## Estructura
```
hacia-playground/
├── api/
│   └── analyze.js      ← proxy seguro a la API de Anthropic
├── public/
│   └── index.html      ← la app completa
├── vercel.json         ← configuración de rutas
└── README.md
```

## Pasos para deployar (5 minutos)

### 1. Crear cuenta en Vercel
Ir a https://vercel.com → Sign up con GitHub (gratis)

### 2. Subir el proyecto
**Opción A — Drag & drop (más fácil):**
1. Ir a https://vercel.com/new
2. Hacer clic en "Browse" o arrastrar la carpeta `hacia-playground`
3. Vercel detecta automáticamente la configuración

**Opción B — GitHub:**
1. Crear repo en GitHub y subir esta carpeta
2. En Vercel → New Project → importar el repo

### 3. Agregar la API key de Anthropic
En el dashboard de Vercel, antes de hacer Deploy:
1. Ir a **Settings → Environment Variables**
2. Agregar:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-...` (tu API key de https://console.anthropic.com)
3. Hacer clic en **Save**

### 4. Deploy
- Hacer clic en **Deploy**
- En ~1 minuto la app estará en una URL tipo: `https://hacia-playground-xxx.vercel.app`

## Costo estimado
- Vercel: **gratis** (plan hobby, suficiente para demos)
- Anthropic API:
  - Haiku (texto puro): ~$0.002 por análisis
  - Sonnet (imágenes/PDF): ~$0.015 por análisis
  - 100 análisis al mes ≈ $0.50–$1.50

## Notas técnicas
- La API key **nunca** queda expuesta en el browser
- El proxy en `api/analyze.js` es el único que tiene acceso a la key
- CORS configurado para aceptar requests desde cualquier origen
- Compatible con el plan Free de Vercel (serverless functions incluidas)
