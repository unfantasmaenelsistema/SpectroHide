# SpectroHide

**Esteganografía de audio para retos CTF**, de [Un Fantasma en el Sistema](https://www.unfantasmaenelsistema.com).

▶ **Abrir:** https://unfantasmaenelsistema.github.io/SpectroHide/

SpectroHide esconde un texto en el **espectrograma** de un archivo de audio: al escucharlo solo se oye un siseo (o la música que elijas de fondo), pero al abrirlo en Audacity, Sonic Visualiser o en la propia herramienta, el texto aparece dibujado en las frecuencias. Es una técnica clásica de los retos de esteganografía.

## Qué hace

**Generar audio**
- Escribe el texto (por ejemplo `CTF{h1dd3n}`), elige la duración, el sample rate (22,05 / 44,1 / 48 kHz) y la banda de frecuencias donde irá el texto.
- Ajusta la intensidad del texto y el ruido de fondo para subir o bajar la dificultad.
- Opcionalmente, mézclalo con un audio base (WAV, MP3 u OGG) para disimularlo.
- Escúchalo, mira la vista previa del espectrograma y descárgalo en WAV de 16 bits.
- Valida la banda: avisa si baja de 100 Hz o supera el límite de Nyquist del sample rate elegido.

**Analizar audio**
- Carga un WAV, FLAC, MP3, OGG o M4A y verás su espectrograma.
- Trabaja a la **frecuencia de muestreo real del archivo**: en un WAV de 96 kHz se ve todo hasta 48 kHz.
- En audios estéreo puedes ver cada canal por separado o la **diferencia L−R**, donde a veces se esconde la pista.
- Escala en dB con ganancia y rango (los mismos valores que Audacity), ventana FFT de 512 a 4096, mapas de color y exportación a PNG.
- Cada columna del espectrograma toma el máximo de varias ventanas, para que no se pierdan sonidos cortos en audios largos.

**Guía de Audacity**: el botón «Ver configuración en Audacity» te da los valores exactos (escala lineal, banda, ventana, ganancia) para que el texto se lea en Audacity sin deformarse.

## Privacidad

Todo ocurre en tu navegador. Los audios no se suben a ningún servidor.

## Uso responsable

Pensada para crear y resolver retos CTF y para aprender esteganografía. No la uses para ocultar contenido con fines ilícitos.

## Estructura

```
index.html   la aplicación (HTML, CSS y JS en un solo archivo)
icono.png    logo de la casa
```

Para probar en local: `python -m http.server` y abre `http://localhost:8000`.

## English

**SpectroHide** hides text in the spectrogram of an audio file for CTF steganography challenges, and analyses audio files to reveal it. It generates 16-bit WAVs (optionally mixed with a base track), validates the band against Nyquist, and shows spectrograms in dB at the file's native sample rate, with per-channel and L−R views. It also gives the exact Audacity settings to read the text. Everything runs in your browser. Bilingual (ES/EN), light/dark themes.

## Licencia / License

[MIT](LICENSE) © Un Fantasma en el Sistema
