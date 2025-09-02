# 📌 Píldora Formativa: Modelos de Difusión y Stable Diffusion

Este proyecto contiene una **presentación técnica y práctica** sobre los modelos de difusión, con especial foco en **Stable Diffusion**, preparada como píldora formativa para el bootcamp.

---

## 🎤 Contenido de la presentación

- **Presentación (Marp)**  
  Explica de manera visual y progresiva:
  - Qué son los modelos de difusión.
  - Fase directa (añadir ruido) y fase inversa (quitar ruido).
  - El papel de la **U-Net**.
  - El concepto de **espacio latente** y su importancia en la eficiencia.
  - Qué hace el **VAE** (encoder/decoder).
  - El condicionamiento con texto e imágenes (prompts).
  - Cómo encajan todas las piezas en **Stable Diffusion**.

Archivo:  
```
presentacion-diffusion.md
```

---

## 🧪 Demos prácticas

### 🔹 Demo 1 – Simulación de difusión (Forward & Reverse)
- Imagen (astronauta o MNIST).
- Forward process → degradación progresiva con ruido.
- Reverse process → limpieza iterativa (filtro gaussiano).
- Sirve para entender el proceso de difusión de forma visual y sencilla.

Archivo:  
```
notebooks/demo1_diffusion.ipynb
```

---

### 🔹 Demo 2 – Autoencoder y espacio latente
- Usamos **MNIST** (dígitos manuscritos).
- Entrenamos un autoencoder sencillo:
  - Encoder → comprime imagen (espacio latente).
  - Decoder → reconstruye la imagen.
- Mostramos:
  - Imágenes originales vs reconstruidas.
  - Interpolación en el espacio latente (ej. transición de un 3 a un 8).

Archivo:  
```
notebooks/demo2_autoencoder_latent.ipynb
```

---

### 🔹 Demo 3 – Stable Diffusion real con Hugging Face
- Usamos `diffusers` de Hugging Face.
- Generamos imágenes reales desde prompts:
  - Ejemplo: *“A dog astronaut painted in Van Gogh style”*.
  - Otros ejemplos: ciudad cyberpunk, castillo medieval, coche futurista.
- Conexión directa con la teoría: CLIP, U-Net, VAE, espacio latente.

Archivo:  
```
notebooks/demo3_stable_diffusion.ipynb
```

---

## 🎮 Kahoot (actividad final)
Como repaso, se preparó un **Kahoot de 11 preguntas** con conceptos clave:
- Forward vs Reverse process.
- U-Net.
- Espacio latente.
- VAE.
- CLIP y condicionamiento.
- Ventajas de Stable Diffusion.

Enlace: 👉 [kahoot.it](https://kahoot.it) (usar PIN que comparta el presentador).  

---

## ⚙️ Requisitos técnicos

### Entorno local
- Python 3.10+  
- Dependencias en `requirements.txt`:
  - `numpy`
  - `matplotlib`
  - `scikit-image`
  - `scipy`
  - `tensorflow`
  - `torch`
  - `diffusers`
  - `transformers`
  - `accelerate`
  - `safetensors`

Instalación:
```bash
pip install -r requirements.txt
```

### Google Colab
Se recomienda ejecutar la **Demo 3** en Colab con GPU habilitada.

---

## 📂 Estructura del repo
```
├── presentacion-diffusion.md   # Presentación en Marp
├── notebooks/
│   ├── demo1_diffusion.ipynb   # Forward & reverse noise
│   ├── demo2_autoencoder_latent.ipynb # Espacio latente
│   └── demo3_stable_diffusion.ipynb   # Hugging Face demo
├── requirements.txt
└── README.md
```

---

## ✨ Créditos
- Presentación y demos preparadas por **César Mercado Hernández**.  
- Inspirado en la documentación oficial de [Stable Diffusion](https://stability.ai/) y [Hugging Face Diffusers](https://huggingface.co/docs/diffusers/index).  
