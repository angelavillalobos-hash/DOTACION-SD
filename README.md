# Asistencia SD

Dashboard operacional de dotación diaria para las estaciones **SRM1** y **SRM2** de Mercado Libre.

---

## Vista previa

> Reporte ejecutivo con fondo oscuro, colores Mercado Libre y gráficos con etiquetas.

---

## Funcionalidades

- **Filtro SRM1 / SRM2 / Combinado** — cambia la vista al instante
- **Fecha en tiempo real** — se actualiza automáticamente al abrir
- **Métricas clave** — capacidad real, solicitada, ausentes y cobertura
- **Gráfico de barras** — cap. real vs. solicitada con etiquetas de valor
- **Gráfico de ausentismo** — con semáforo de colores (verde / amarillo / rojo)
- **Tabla de detalle** — por ítem con observaciones y badges de estado
- **Conexión a Google Sheets** — intenta leer datos en vivo al cargar
- **Actualización manual** — botón para refrescar datos en cualquier momento
- **Descarga como PNG** — genera imagen lista para enviar por WhatsApp o correo

---

## Tecnologías

| Librería | Uso |
|---|---|
| [Chart.js 4.4](https://www.chartjs.org/) | Gráficos de barras |
| [html2canvas 1.4](https://html2canvas.hertzen.com/) | Exportar a imagen PNG |
| Anthropic MCP + Google Drive | Lectura live del Google Sheet |

---

## Uso

### Opción 1 — GitHub Pages (recomendado)

1. Ve a **Settings → Pages**
2. En *Branch* selecciona `main` y carpeta `/root`
3. Guarda — en unos segundos tendrás una URL pública:
   ```
   https://<tu-usuario>.github.io/<nombre-repo>
   ```

### Opción 2 — Local

Abre directamente `index.html` en tu navegador. No requiere servidor.

---

## Conexión al Google Sheet

El dashboard intenta leer la planilla en tiempo real a través de la API de Anthropic + Google Drive MCP.

- ✅ **Punto verde** — datos actualizados desde el Sheet
- 🟡 **Punto amarillo** — cargando o usando datos locales
- 🔴 **Punto rojo** — sin conexión, mostrando último snapshot conocido

> **Nota:** la conexión live funciona cuando el dashboard se abre desde un entorno con sesión Anthropic activa (ej. claude.ai). Desde GitHub Pages cargará el snapshot local por defecto.

---

## Personalización

Para apuntar a otro Google Sheet, cambia el valor de `SHEET_ID` en el `<script>` de `index.html`:

```js
const SHEET_ID = 'TU_SHEET_ID_AQUI';
```

El ID se encuentra en la URL de la planilla:
```
https://docs.google.com/spreadsheets/d/[SHEET_ID]/edit
```

---

## Estructura del repo

```
/
└── index.html    — dashboard completo (HTML + CSS + JS en un solo archivo)
└── README.md     — este archivo
```

---

*Desarrollado para el equipo SD · Mercado Libre Chile*
