# 🔐 Streamlit Hash Demo — SHA-256 / SHA-1 / SHA-512 / BLAKE2 + Salt / Pepper + HMAC

App didáctica para comprender **funciones hash criptográficas**, integridad de datos y autenticación básica mediante **HMAC**.  
Diseñada para funcionar **100% en la nube** usando **GitHub + Streamlit Community Cloud**, sin necesidad de instalar nada localmente.

---

## 🚀 Características

- **Algoritmos soportados:** `sha256` (por defecto), `sha1`, `sha512`, `blake2b`
- **Hash de texto y archivos** (hash incremental con barra de progreso)
- **Comparación de hashes** (segura, constante en tiempo)
- **Salting** (sal pública) y **Peppering** (secreto en `st.secrets`)
- **HMAC** con clave secreta (`st.secrets["HMAC_KEY"]`)
- **Exportación CSV** de resultados de la sesión

> ⚠️ **Nota:** un hash **no es cifrado**. No permite recuperar el texto original. SHA-1 tiene colisiones conocidas y se usa solo con fines educativos.

---

## 🧩 Estructura del repositorio

streamlit-hash-demo/
├─ README.md
├─ requirements.txt
├─ app.py
├─ hash_utils.py
├─ tests/
│ └─ test_hash_utils.md
└─ assets/
└─ example.txt


---

## 💻 Uso rápido (demo)

1. Escribe un texto en el campo principal y selecciona un algoritmo (por defecto: `sha256`).
2. Activa **Añadir sal** para generar una sal aleatoria o pegar una en hex.
3. Activa **Usar pepper** (si tienes `PEPPER` configurado en `st.secrets`).
4. Sube un archivo y observa la **barra de progreso** del hash incremental.
5. Usa la pestaña **Comparar** para verificar si dos hashes son idénticos.
6. Genera/verifica **HMAC** usando una clave secreta (`HMAC_KEY`).
7. Descarga todos los resultados en formato **CSV** desde la pestaña final.

---

## ☁️ Despliegue en Streamlit Cloud (solo navegador)

1. Crea un repositorio en GitHub llamado **`streamlit-hash-demo`**
   - Rama principal: `main`
   - `.gitignore` → Python
   - Licencia → MIT

2. Añade los archivos del proyecto (`README.md`, `requirements.txt`, `app.py`, `hash_utils.py`, etc.).

3. Ve a 👉 [https://share.streamlit.io/new](https://share.streamlit.io/new)
   - Haz clic en **“Deploy an app”**
   - Autoriza GitHub
   - Selecciona tu repo y `app.py` como archivo principal

4. Configura los secretos:
   - En la app de Streamlit → **⋯ → Settings → Secrets**
   - Añade lo siguiente:

     ```toml
     PEPPER = "cambia-esto-por-un-secreto-largo-aleatorio"
     HMAC_KEY = "otra-clave-secreta-larga-para-hmac"
     ```

5. Guarda y **Deploy**.  
   ¡Listo! Tu app estará disponible con su propia URL pública.

---

## 🔐 Buenas prácticas

- **Hash ≠ cifrado:** no se puede revertir.
- **Sal:** pública, aleatoria y única por entrada (16 bytes mínimo).
- **Pepper:** secreto del servidor (nunca en BD ni CSV).
- **HMAC:** garantiza integridad **y** autenticidad (clave compartida).
- **SHA-1:** solo para fines didácticos.
- **Contraseñas reales:** usar **Argon2**, **PBKDF2** o **scrypt** con iteraciones.

---

## 🧪 Verificación manual

| Acción | Entrada | Algoritmo | Resultado esperado |
|--------|----------|------------|--------------------|
| Hash texto “hello” | — | SHA-256 | `2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824` |
| HMAC (“hello”, clave=”key”) | — | SHA-256 | `9307b3b915efb5171ff14d8cb55fbcc798c6c0ef1456d66ded1a6aa0f1f7c9d0` |
| Comparación | Dos hashes idénticos | — | ✅ Coinciden |
| Comparación | Diferentes | — | ❌ No coinciden |

---

## 🧰 Requisitos

streamlit==1.37.0


> No se requiere ninguna instalación local. Todo se ejecuta en la nube.

---

## 🛠️ Extensiones futuras

- Hashes en árbol (tipo **Merkle**)
- Soporte de múltiples archivos drag&drop
- Integración con URLs o API REST
- Logging educativo (sin datos sensibles)
- Uso de Argon2/scrypt para contraseñas

---

## 📝 Licencia

MIT © 2025  
Proyecto educativo — creado para prácticas de **Seguridad, IoT y Blockchain**.

---

## 💬 Mensaje de commit sugerido

feat: primera versión app de hashing con salt/pepper y HMAC


---

## 🔎 Descripción corta del repositorio

> App educativa de Streamlit para hashing de textos y archivos (SHA-256/1/512/BLAKE2), con sal, pepper, HMAC y exportación CSV. 100% desplegable en Streamlit Cloud desde GitHub.

