# AI Architecture Playground â Deploy en Vercel

## Estructura
```
hacia-playground/
âââ api/
â   âââ analyze.js      â proxy seguro a la API de Anthropic
âââ public/
â   âââ index.html      â la app completa
âââ vercel.json         â configuraciÃ³n de rutas
âââ README.md
```

## Pasos para deployar (5 minutos)

### 1. Crear cuenta en Vercel
Ir a https://vercel.com â Sign up con GitHub (gratis)

### 2. Subir el proyecto
**OpciÃ³n A â Drag & drop (mÃ¡s fÃ¡cil):**
1. Ir a https://vercel.com/new
2. Hacer clic en "Browse" o arrastrar la carpeta `hacia-playground`
3. Vercel detecta automÃ¡ticamente la configuraciÃ³n

**OpciÃ³n B â GitHub:**
1. Crear repo en GitHub y subir esta carpeta
2. En Vercel â New Project â importar el repo

### 3. Agregar la API key de Anthropic
En el dashboard de Vercel, antes de hacer Deploy:
1. Ir a **Settings â Environment Variables**
2. Agregar:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-...` (tu API key de https://console.anthropic.com)
3. Hacer clic en **Save**

### 4. Deploy
- Hacer clic en **Deploy**
- En ~1 minuto la app estarÃ¡ en una URL tipo: `https://hacia-playground-xxx.vercel.app`

## Costo estimado
- Vercel: **gratis** (plan hobby, suficiente para demos)
- Anthropic API:
  - Haiku (texto puro): ~$0.002 por anÃ¡lisis
  - Sonnet (imÃ¡genes/PDF): ~$0.015 por anÃ¡lisis
  - 100 anÃ¡lisis al mes â $0.50â$1.50

## Notas tÃ©cnicas
- La API key **nunca** queda expuesta en el browser
- El proxy en `api/analyze.js` es el Ãºnico que tiene acceso a la key
- CORS configurado para aceptar requests desde cualquier origen
- Compatible con el plan Free de Vercel (serverless functions incluidas)

<!-- redeploy 1775353459008 -->