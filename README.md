# 🍲 Cocina Vicuy

**App web progresiva (PWA) para planear comidas**: despensa, recetario y menú semanal con lista de mercado automática. Sincroniza entre dispositivos en tiempo real y funciona sin conexión.

🔗 **Demo:** [scmelor.github.io/Mi-Cocina](https://scmelor.github.io/Mi-Cocina/) *(abre la cocina pública "demo"; cualquiera puede editarla)*

<p align="center">
  <img src="docs/mercado.png" alt="Despensa por categorías" width="32%">
  <img src="docs/recetas.png" alt="Recetario" width="32%">
  <img src="docs/menu.png" alt="Menú semanal" width="32%">
</p>

---

## ✨ Funcionalidades

- **Mercado:** despensa por categorías personalizables. Marcas lo que tienes en casa.
- **Recetas:** colombianas, venezolanas, del mundo y propias, con favoritos.
- **Búsqueda combinada:** recetas propias + [TheMealDB](https://www.themealdb.com/) + [Spoonacular](https://spoonacular.com/food-api) (opcional), con traducción automática al español.
- **Menú semanal:** genera almuerzo, ensalada y cena según lo que hay en la despensa y excluye los ingredientes que no te gustan.
- **Lista de mercado** generada a partir del menú.
- **Historial** de semanas guardadas para reutilizarlas.
- **Sinónimos de ingredientes** (ej. *shrimp = camarón*) para reconocer recetas en otros idiomas.
- **Perfil** con nombre y foto de la cocina.

## 🛠️ Tecnologías

| Área | Herramientas |
|---|---|
| Frontend | HTML5, CSS3, JavaScript (ES6+), sin frameworks |
| Datos en tiempo real | Firebase Realtime Database |
| APIs externas | TheMealDB, Spoonacular (`fetch` + caché local) |
| PWA | Web App Manifest y Service Worker (instalable, funciona sin conexión) |
| Despliegue | GitHub Pages |

## 🔐 Seguridad y privacidad

- Los datos se guardan en **"salas"** identificadas por un **código de cocina**.
- Las reglas de Realtime Database ([`database.rules.json`](database.rules.json)) solo permiten la sala pública `demo` o códigos de **12 caracteres o más**. No se puede listar la base completa, así que nadie puede descubrir otras salas.
- La **clave de Spoonacular no está en el código**: cada usuario pega la suya en ⚙️ y queda guardada solo en su navegador.

```json
"rooms": { "$room": {
  ".read":  "$room === 'demo' || $room.length >= 12",
  ".write": "$room === 'demo' || $room.length >= 12"
}}
```

## 🧠 Qué aprendí

- Integrar **varias APIs REST** y unificar sus resultados con caché local.
- Sincronizar estado en **tiempo real** entre dispositivos con listeners de Firebase.
- Diseñar **reglas de seguridad** y sacar las claves privadas del código fuente.
- Construir un algoritmo de **generación de menús** con restricciones (despensa, gustos, variedad).

## 🚀 Ejecutar tu propia copia

1. Haz un *fork* o descarga el repositorio.
2. Crea un proyecto en [Firebase](https://console.firebase.google.com) y activa **Realtime Database**.
3. En **Reglas**, pega el contenido de `database.rules.json` y publica.
4. En `index.html`, reemplaza `MI_FIREBASE` por la configuración web de tu proyecto.
5. Activa **GitHub Pages** (Settings → Pages → `main` / root).
6. En la app: ⚙️ → **Código de cocina** → escribe un código privado de 12 caracteres o más y úsalo igual en todos tus dispositivos.
7. (opcional) ⚙️ → **Búsqueda avanzada** → pega tu clave gratuita de Spoonacular.

### Instalar en el celular

- **Android (Chrome):** menú ⋮ → *Instalar aplicación*.
- **iPhone (Safari):** Compartir → *Agregar a inicio*.

---

Desarrollado por **Silvia Melo** · [github.com/Scmelor](https://github.com/Scmelor)
