# English Trainer (PWA)

Esto convierte tus dos juegos (phrasal verbs y vocabulario) en **una app móvil tipo PWA**:
- Funciona offline (service worker).
- Se instala en Android/iOS como “app” (pantalla de inicio).
- Mantiene estadísticas y fallos por mazo (localStorage).

## Estructura
- `web/index.html` (app)
- `web/manifest.webmanifest`
- `web/sw.js`
- `web/icon-192.png`, `web/icon-512.png`

## Probar en PC
```bash
cd web
python -m http.server 8000
```
Abre: http://127.0.0.1:8000

## Instalar en móvil (PWA)
### Android (Chrome)
1. Abre la URL en Chrome.
2. Menú ⋮ → **Instalar aplicación**.

### iOS (Safari)
1. Abre la URL en Safari.
2. Compartir → **Añadir a pantalla de inicio**.

> Nota: para que el modo offline funcione fuera de localhost, necesitas servirlo por HTTPS (GitHub Pages/Netlify/etc.).

## (Opcional) Convertir a APK / App Store (wrapper nativo)
La forma más directa es **Capacitor**:
1. Crea proyecto:
```bash
mkdir en-trainer-cap
cd en-trainer-cap
npm init -y
npm i @capacitor/core @capacitor/cli
npx cap init "English Trainer" "com.tuusuario.entrainer" --web-dir=web
```
2. Copia la carpeta `web/` de este repo dentro de `en-trainer-cap/web/`.
3. Android:
```bash
npx cap add android
npx cap sync android
npx cap open android
```
4. iOS (en macOS):
```bash
npx cap add ios
npx cap sync ios
npx cap open ios
```

## Editar / añadir vocabulario
Edita directamente el JSON embebido en `index.html` (constante `DECKS`) o, si prefieres, dime y lo separo en `decks/phrasal.json` y `decks/vocab.json`.
