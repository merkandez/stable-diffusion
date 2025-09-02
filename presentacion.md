---
marp: true
theme: default
paginate: true
---

# 🌌 Modelos de Difusión y Stable Diffusion
### Cómo las máquinas generan imágenes a partir de texto

<!--
Notas:
Imagina pedir a una IA: “Dibuja un perro astronauta al estilo Van Gogh”.  
Y la IA lo crea desde ruido puro.  
Eso es lo que vamos a explicar hoy: los modelos de difusión y cómo Stable Diffusion lo hace posible.
-->

🖼️ Imagen sugerida: una obra generada con Stable Diffusion (ej. astronauta + estilo artístico).  

---

# 🤖 ¿Qué son los modelos generativos?
- Crean nuevos datos que parecen reales.  
- Aprenden de un dataset.  
- En nuestro caso → imágenes.  

👉 Imaginan a partir de ruido.

<!--
Notas:
Los modelos generativos no se limitan a reconocer patrones: crean ejemplos nuevos.  
Stable Diffusion pertenece a esta familia.
-->

🖼️ Imagen sugerida: diagrama con “Dataset → Modelo → Nuevas imágenes”.

---

# 🔄 El proceso de difusión
Dos fases:  
1. Difusión directa → añadir ruido.  
2. Difusión inversa → quitar ruido.

<!--
Notas:
La clave es un proceso en dos fases: destruir (añadiendo ruido) y reconstruir (quitando ruido).
-->

🖼️ Usa tu captura **sd13.png** (imagen → ruido progresivo).

---

# 🌫️ Difusión directa
Imagen clara → ruido paso a paso → ruido total  

👉 Como empañar una ventana.

<!--
Notas:
Primera fase: añadir ruido gaussiano progresivamente hasta que la imagen queda irreconocible.
-->

🖼️ Usa tu captura **sd14.png** (ruido en aumento).  

---

# ✨ Difusión inversa
Ruido total → eliminación progresiva → imagen reconstruida  

👉 Como desempañar la ventana.

<!--
Notas:
La parte difícil: aprender a quitar el ruido paso a paso.  
Aquí entra la U-Net.
-->

🖼️ Usa tu captura **sd18.png** (ruido → imagen).  

---

# 🧠 La red U-Net
- Predice cuánto ruido quitar en cada paso.  
- Entrada: imagen ruidosa.  
- Salida: ruido estimado.  
- Permite generar desde ruido puro.

<!--
Notas:
La U-Net es la red central: su arquitectura en forma de U extrae y reconstruye características, prediciendo el ruido.
-->

🖼️ Imagen sugerida: esquema de U-Net (encogimiento → expansión con skip connections).  

---

# 🎨 Condicionamientos
El modelo necesita control creativo:  
- Texto (prompts).  
- Imágenes de referencia.  
- Máscaras de edición.  
- Mapas de profundidad.

👉 Como dar instrucciones a un pintor.

<!--
Notas:
Los condicionamientos guían el proceso.  
CLIP transforma el texto en vectores que guían a la U-Net.
-->

🖼️ Imagen sugerida: prompt → imagen.  

---

# ⚡ Coste computacional
Problema de los modelos clásicos:  
- Operan en píxeles.  
- Imagen 512×512 RGB ≈ 800.000 valores.  
- Muy lentos y pesados.

<!--
Notas:
Trabajar en píxeles hacía los modelos lentísimos e inviables para usuarios comunes.
-->

🖼️ Imagen sugerida: gráfico con muchos píxeles / dataset pesado.  

---

# 💡 Espacio latente
- Stable Diffusion opera en un espacio comprimido.  
- Representa lo esencial de la imagen.  
- Más rápido y eficiente.

👉 Como usar un mapa en lugar de recorrer toda la ciudad.

<!--
Notas:
El espacio latente reduce el problema a menos dimensiones sin perder lo importante.
-->

🖼️ Usa tu captura **3b8332e3.png** (esquema latente).  

---

# 🌀 VAE (Variational Autoencoder)
- **Encoder (E):** convierte a espacio latente.  
- **Decoder (D):** reconstruye la imagen.  

👉 El VAE es el traductor entre píxeles y latente.

<!--
Notas:
El VAE hace posible trabajar en latente.  
Encoder → comprime.  
Decoder → reconstruye.
-->

🖼️ Usa tu captura **56633feb.png** (encoder/decoder).  

---

# 🔗 Unión de elementos
Stable Diffusion combina:  
- Difusión latente (eficiencia).  
- U-Net (ruido).  
- Condicionamientos (control creativo).  
- VAE (traducción).  
- CLIP (texto → vector).  

<!--
Notas:
La fuerza de Stable Diffusion está en juntar todas estas piezas.  
Así se logra un modelo ligero, potente y abierto.
-->

🖼️ Imagen sugerida: esquema integrador con todas las piezas.  

---

# 🚀 Stable Diffusion
- **Ligero**: se ejecuta en PCs con GPU.  
- **Versátil**: texto, imágenes, máscaras.  
- **Open Source**: comunidad de mejoras.  

---

# 🌍 Aplicaciones y futuro
✅ Arte y diseño  
✅ Marketing  
✅ Videojuegos y cine  
✅ Medicina e investigación  

⚠️ Riesgos: deepfakes, copyright, sesgos  

<!--
Notas:
Aquí puedes abrir debate sobre riesgos y futuro multimodal: texto + imagen + audio + vídeo.
-->

🖼️ Imagen sugerida: collage de aplicaciones (arte, cine, medicina).  

---

# ❓ Pregunta final
¿Dónde ponemos los límites al uso de estas herramientas?

<!--
Notas:
Cierra con una pregunta abierta para fomentar reflexión y debate.
-->
