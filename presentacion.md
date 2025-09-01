---
marp: true
theme: default
paginate: true
---

# 🌌 Modelos de Difusión y Stable Diffusion
### Cómo las máquinas generan imágenes a partir de texto

<!--
Notas:
Bienvenidos a esta píldora formativa.  
Hoy vamos a descubrir qué son los modelos de difusión, cómo funcionan en teoría, cómo se aplican a imágenes y qué hace que Stable Diffusion sea tan especial.  
El objetivo es que todos entendamos el concepto desde cero, pero también que veamos su parte técnica y práctica.
-->

---

# 🤖 ¿Qué son los modelos de difusión?
- Modelos **generativos** de Deep Learning.  
- Diseñados para **crear nuevos datos** a partir de lo aprendido.  
- En el caso de Stable Diffusion → **imágenes**.  

<!--
Notas:
Stable Diffusion pertenece a la familia de modelos de difusión.  
Estos modelos son generativos, es decir, crean nuevos datos que se parecen a los ejemplos que vieron durante su entrenamiento.  
En nuestro caso, hablamos de imágenes. Pero la idea general también se aplica a audio, vídeo o incluso moléculas.
-->

---

# 🔄 El proceso de difusión
- **Dos fases principales**:
  1. Difusión directa → añadir ruido progresivo.
  2. Difusión inversa → eliminar el ruido paso a paso.  

---

# 🌫️ Fase 1: Difusión directa
Imagen → Ruido paso a paso → Imagen irreconocible

<!--
Notas:
En la fase directa, cogemos una imagen del dataset y le vamos añadiendo ruido gaussiano.  
Al principio la imagen todavía se reconoce, pero a medida que añadimos más pasos se va desfigurando hasta volverse puro ruido.  
Este proceso se puede hacer matemáticamente sin problema.
-->

---

# ✨ Fase 2: Difusión inversa
Ruido → Eliminación progresiva → Imagen reconstruida

<!--
Notas:
La parte difícil llega cuando intentamos revertir el proceso.  
¿Cómo sabemos cuánto ruido quitar en cada paso?  
¿Cuántos pasos necesitamos?  
Para resolverlo, se entrena una red neuronal especializada que predice el nivel de ruido en cada iteración.
-->

---

# 🧠 La red U-Net
- Arquitectura clave en la fase inversa.  
- Aprende a predecir **qué ruido quitar** en cada paso.  
- Entrada: imagen ruidosa.  
- Salida: estimación de ruido.  

<!--
Notas:
Aquí aparece la red U-Net.  
Es una arquitectura muy usada en visión por computadora porque combina una parte de contracción (extraer características) con una de expansión (reconstrucción).  
En Stable Diffusion, su papel es predecir el ruido que hay que eliminar.  
Gracias a U-Net podemos partir de una nube de ruido puro y acabar con una imagen coherente.
-->

---

# 🎨 Condicionamientos
- El modelo necesita **control creativo**.  
- Tipos de condicionamiento:
  - Texto (prompt).  
  - Mapas de profundidad.  
  - Máscaras de edición.  
  - Imágenes de referencia.  

<!--
Notas:
El modelo por sí mismo solo denoisea, pero no sabe qué imagen generar.  
Para guiarlo usamos condicionamientos.  
El más famoso: los prompts de texto. Escribir “un perro astronauta en estilo Van Gogh” hace que la U-Net reconstruya el ruido en esa dirección.  
Pero también se pueden usar mapas de profundidad, máscaras para editar partes de la imagen, o incluso imágenes de referencia.  
Esto es lo que hace que podamos tener un control casi artístico sobre el proceso.
-->

---

# ⚡ El problema de los costes
- Modelos clásicos trabajan en **espacio de píxeles**.  
- Ejemplo: imagen 512×512 RGB = ~800.000 valores.  
- Añadir/quitar ruido sobre todos esos valores → **muy lento y costoso**.  

<!--
Notas:
Los modelos de difusión originales operaban directamente sobre los píxeles de la imagen.  
El problema es que una sola imagen de 512×512 píxeles y tres canales de color implica manejar casi un millón de valores.  
Y recordad que el proceso de difusión implica cientos o miles de pasos.  
Esto hace que los cálculos sean muy pesados y lentos.
-->

---

# 💡 La innovación: espacio latente
- Stable Diffusion introduce los **Modelos de Difusión Latente**.  
- En lugar de trabajar con píxeles, lo hace en un espacio matemático **comprimido**.  
- Beneficio: **eficiencia y rapidez**.  

<!--
Notas:
La solución de Stability AI fue operar en un espacio más compacto: el espacio latente.  
Aquí la imagen se representa en menos dimensiones, lo que reduce drásticamente los cálculos.  
En lugar de trabajar con todos los píxeles, trabajamos con una versión comprimida que conserva la esencia visual.
-->

---

# 🌀 El papel del VAE
- **Variational Autoencoder (VAE)**: red con dos partes.
  - **Encoder (E):** lleva la imagen al espacio latente.  
  - **Decoder (D):** reconstruye la imagen desde el espacio latente.  

<!--
Notas:
Para movernos entre el espacio de píxeles y el espacio latente necesitamos un VAE.  
El encoder comprime la imagen en una representación abstracta, y el decoder la reconstruye después.  
Así todo el proceso de difusión ocurre en el espacio latente, y solo al final recuperamos la imagen visible.
-->

---

# 🔗 Uniendo todo
Stable Diffusion combina:
- Difusión en espacio latente (eficiencia).  
- U-Net (predicción del ruido).  
- Condicionamientos (control creativo).  

<!--
Notas:
Si juntamos todas las piezas tenemos Stable Diffusion:  
1. Un modelo eficiente gracias al espacio latente.  
2. Preciso gracias a la U-Net que elimina el ruido.  
3. Creativo y versátil gracias a los condicionamientos.  
El resultado es un modelo ligero, versátil y open source.
-->

---

# 🚀 Stable Diffusion
- **Ligero**: puede ejecutarse en PCs con GPU común.  
- **Versátil**: soporta texto, imágenes, máscaras.  
- **Open Source**: la comunidad crea y mejora variantes.  

<!--
Notas:
Por todo esto Stable Diffusion se volvió revolucionario en 2022.  
No solo democratizó el acceso a la IA generativa de imágenes, sino que al ser open source, miles de personas han creado sus propias variantes.  
Hoy existen modelos especializados en retratos, anime, arquitectura, medicina, etc.
-->

---

# 🌍 Aplicaciones y futuro
✅ Arte y diseño  
✅ Marketing y creatividad  
✅ Videojuegos  
✅ Medicina e investigación  
⚠️ Riesgos: deepfakes, copyright, sesgos  

<!--
Notas:
Las aplicaciones son enormes: desde arte digital y videojuegos, hasta investigación médica.  
Pero no podemos olvidar los riesgos: la creación de deepfakes, problemas de copyright, y los sesgos en los datos de entrenamiento.  
El futuro apunta a modelos multimodales capaces de trabajar no solo con imágenes, sino también con audio y vídeo.
-->

---

# 📚 Conclusión
- Los modelos de difusión generan imágenes **a partir de ruido**.  
- Stable Diffusion lo hace **eficiente** en espacio latente.  
- Nos da **control creativo** mediante condicionamientos.  
- Y es **open source**, impulsando una gran comunidad.  

<!--
Notas:
Cerramos con un resumen:  
1. Los modelos de difusión son capaces de imaginar a partir de ruido.  
2. Stable Diffusion optimiza este proceso en el espacio latente.  
3. Gracias a los condicionamientos podemos guiar la creatividad.  
4. Y al ser open source, se ha convertido en un estándar de la comunidad.  
La idea final: lo que antes era ciencia ficción, hoy está al alcance de cualquiera con un ordenador.
-->
