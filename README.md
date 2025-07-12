# Estimador de Story Points - Adaptación de Contenidos eLearning

Este proyecto es una herramienta web ligera que permite estimar el tiempo de procesamiento de solicitudes de adaptación de contenidos eLearning utilizando **Story Points**.

## 📦 Estructura del repositorio

```
/ (raíz)
├── index.html      # Interfaz principal y lógica de cálculo
├── tailwind.css    # (opcional) estilos si se precompilan localmente
└── README.md       # Documentación de uso y lógica de cálculo
```

## 🚀 Cómo usar

1. Clona el repositorio:

   ```bash
   git clone https://github.com/tu-usuario/estimador-storypoints.git
   cd estimador-storypoints
   ```
2. Abre `index.html` en tu navegador preferido.
3. Al cargar la página, verás un modal con:

   * Puntos asignados a cada elemento (paths, módulos, contenido y adaptaciones).
   * Velocidad de procesamiento (4 SP por día hábil).
   * Cierra el modal para comenzar a usar la herramienta.
4. Define el **número de Learning Paths** y haz clic en **Calcular Estimación** para ver el total de Story Points y el equivalente en días hábiles.

## ⚙️ Lógica de cálculo

La estimación se basa en estos componentes:

| Elemento                    | Story Points (SP) |
| --------------------------- | ----------------- |
| **Learning Path**           | 2 SP cada uno     |
| **Módulo**                  | 1 SP cada uno     |
| **Tipos de contenido**      |                   |
| - SCORM / H5P               | 3 SP              |
| - PowerPoint / Video        | 2 SP              |
| - PDF / Texto / Otro        | 1 SP              |
| **Adaptaciones (checkbox)** |                   |
| - Carga sin modificación    | 0 SP              |
| - Conversión de formato     | 1 SP              |
| - Edición multimedia        | 2 SP              |
| - Navegación                | 1 SP              |
| - Corrección                | 1 SP              |
| - Multilingüe               | 3 SP              |

* **Configuración por defecto**:

  * `setupPointsPath = 2` SP por Learning Path.
  * `setupPointsModule = 1` SP por Módulo.
* **Velocidad de procesamiento**: `pointsPerDay = 4` SP / día hábil.

### Fórmula final

```js
totalSP = (nPaths × 2)
        + (nModules × 1)
        + ∑(SP_tipoContenido + Σ SP_adaptaciones)

díasHábiles = totalSP / 4
```

## 🔧 Personalización

* **Ajustar valores**: modifica las constantes en el `<script>`:

  * `storyPointsContent`
  * `storyPointsAdaptation`
  * `setupPointsPath`
  * `setupPointsModule`
  * `pointsPerDay`
* **Estilos**: usa Tailwind CSS vía CDN o compílalo como PostCSS plugin para producción.

## 🛠️ Requisitos

* Navegador moderno con soporte ES6.
* Conexión opcional para Tailwind CDN.

## 📄 Licencia

MIT © Tu Nombre
