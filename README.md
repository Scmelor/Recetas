# 🍲 Cocina Vicuy

App web (PWA) para planear tus comidas: **Mercado** (despensa por categorías), **Recetas** (colombianas, venezolanas, del mundo y propias) y **Menú semanal** con lista de mercado. Almuerzo, ensalada y cena para 1–2 personas, con prioridad a las carnes.

Funciona en el celular y el computador, se puede **instalar como app**, y se **sincroniza** entre tus dispositivos. La sincronización y la búsqueda avanzada ya vienen **configuradas dentro del archivo**: no hay que pegar ninguna clave.

---

## 📁 Archivos del proyecto (súbelos todos a la raíz del repo)

- `index.html` — la aplicación.
- `manifest.json` — datos de la PWA.
- `sw.js` — service worker (funciona sin conexión).
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` — íconos de la app.

> Para que se instale como app, deben estar **los 6 archivos** en la misma carpeta (la raíz del repositorio).

---

## 🚀 Publicar / actualizar en GitHub

1. Entra a tu repositorio en **github.com**.
2. **Add file → Upload files**, arrastra los archivos (los 6 la primera vez; luego solo los que cambies) y pulsa **Commit changes**.
3. La primera vez, activa GitHub Pages: **Settings → Pages → Deploy from a branch → main → /root → Save**. Aparecerá tu link:
   `https://TU-USUARIO.github.io/TU-REPO/`
4. Cada vez que actualices, abre el link y fuerza recarga con **Ctrl+F5** (en el celular, cierra y reabre la pestaña o la app).

---

## 📲 Instalar como aplicación

- **Android (Chrome):** abre el link → aviso **“Instalar app”**, o menú ⋮ → **Instalar aplicación**.
- **iPhone (Safari):** abre el link en Safari → **Compartir** → **Agregar a inicio**.

Se instala con su ícono y se abre en pantalla completa. Al estar sincronizada, tu menú y recetas se ven igual en todos tus dispositivos.

---

## 🔑 Código de cocina (privacidad)

Tu información (mercado, menú, recetas) se guarda en una “sala” identificada por un **código de cocina**. Para cambiarlo, entra a **⚙️ (arriba a la derecha) → Código de cocina** y guarda uno único y personal (por ejemplo con números). Úsalo igual en todos tus dispositivos. Quien no conozca ese código no puede ver ni modificar tus recetas.

> El código por defecto viene fijado en `index.html` (busca `const MI_CODIGO = "…"` al inicio del archivo) por si quieres dejar uno permanente.

---

## 🔧 Mantenimiento

- **Reglas de Firebase (importante):** las reglas en “modo de prueba” caducan a los ~30 días. Si un día deja de sincronizar, entra a **console.firebase.google.com → tu proyecto → Realtime Database → Rules**, pega esto y pulsa **Publish**:

  ```json
  { "rules": { ".read": true, ".write": true } }
  ```

- **Menú semanal:** una vez generado, se queda hasta que generes uno nuevo (no cambia solo al abrir la app).
- **Búsqueda:** combina tus recetas locales + Spoonacular + TheMealDB. La búsqueda avanzada ya viene activa.

---

Hecho con ♥ para cocinar rico.
