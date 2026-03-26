# Estadio Atletico — WebAR
## Cualquier celular, sin instalar app

---

## PASO 1 — Exportar el modelo desde Unity

1. Abre tu proyecto Unity (IoT-CanchaDeFutbol)
2. Instala el paquete **glTFast** desde Package Manager:
   Window → Package Manager → + → "Add package by name":
   `com.unity.cloud.gltfast`
3. En la jerarquía, selecciona **Estadio_Atletico** (el objeto raíz)
4. Menú → **File → Export → Export to glTF (.glb)**
   - Format: Binary (.glb)
   - Incluir: Meshes, Materials, Textures
5. Guarda como `estadio.glb`
6. Copia `estadio.glb` a esta carpeta (junto al index.html)

> Alternativa gratuita sin paquete: instala el plugin
> "UnityGLTF" desde https://github.com/KhronosGroup/UnityGLTF

---

## PASO 2 — Publicar en GitHub Pages (hosting HTTPS gratis)

WebAR requiere HTTPS. GitHub Pages lo da gratis.

1. Crea cuenta en https://github.com (si no tienes)
2. Crea un repositorio nuevo, p.ej. `estadio-ar` (público)
3. Sube estos archivos al repositorio:
   - `index.html`
   - `estadio.glb`
4. Ve a Settings → Pages
5. Source: **Deploy from a branch** → branch: `main` → `/root`
6. Guarda. En ~2 minutos tu URL será:
   `https://TU_USUARIO.github.io/estadio-ar/`

---

## PASO 3 — Generar el QR

1. Ve a https://qr.io o https://www.qrcode-monkey.com (gratuitos)
2. Pega la URL de tu GitHub Pages
3. Descarga el QR en PNG
4. Imprime o muestra en pantalla

---

## PASO 4 — Imprimir el marcador Hiro

El marcador Hiro es la imagen que la cámara detecta para
saber dónde colocar el modelo 3D.

Descárgalo aquí (oficial AR.js):
https://jeromeetienne.github.io/AR.js/data/images/HIRO.jpg

- Imprime en papel blanco, mínimo 8x8 cm
- También puedes mostrarlo en una segunda pantalla

---

## PASO 5 — Usar la AR

1. Escanea el QR con cualquier celular
2. El navegador pedirá permiso para la cámara → Permitir
3. Apunta al marcador Hiro impreso
4. El estadio aparece en 3D encima del marcador

Funciona en:
- Android: Chrome
- iPhone: Safari (iOS 11+)
- Cualquier navegador moderno con WebRTC

---

## Ajustar tamaño del modelo

Si el estadio se ve muy grande o muy pequeño, edita en index.html:

```html
scale="0.02 0.02 0.02"   ← aumenta o reduce este número
```

Valores de referencia:
- Modelo muy grande (cientos de metros en Unity): 0.005
- Modelo mediano: 0.02
- Modelo pequeño: 0.1

---

## Estructura de archivos

```
webar_estadio/
├── index.html      ← La experiencia AR completa
├── estadio.glb     ← Tu modelo exportado desde Unity
└── README.md       ← Esta guía
```

---

## Troubleshooting

| Problema | Solución |
|----------|----------|
| No detecta el marcador | Mejor iluminación, marcador más grande |
| Modelo no aparece | Verificar que estadio.glb está en la misma carpeta |
| Error de cámara | Asegúrate de abrir desde HTTPS (GitHub Pages) |
| Modelo muy oscuro | En Unity, bake los materiales antes de exportar |
| Modelo girado | Cambia `rotation="-90 0 0"` a `rotation="0 0 0"` |
