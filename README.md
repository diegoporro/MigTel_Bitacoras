# 🚀 MigTel - Sistema de Gestión de Instalaciones, Trabajos y Nómina

Sistema web integral desarrollado para **MigTel** diseñado para la gestión, registro y control de instalaciones técnicas, asignaciones de trabajos especiales y cálculo automatizado de nómina por técnicos y regiones de servicio.

La aplicación utiliza un esquema **Serverless & Cloud Database** conectando un Frontend en **HTML5/JS** alojado en **GitHub Pages** con **Google Sheets** a través de **Google Apps Script (API Web)** como base de datos en tiempo real almacenada en **Google Drive**.

---

## 📋 Características Principales

### 📊 Dashboard Principal
- **Métricas en Tiempo Real:** Indicadores clave con total de instalaciones diarias, semanales y mensuales.
- **Estadísticas de Personal:** Conteo de técnicos activos agrupados por organización/región.
- **Gráfica de Distribución por Región:** Visualización gráfica circular (*Pie Chart*) del volumen de instalaciones repartidas en las 5 zonas operativas.
- **Resumen Financiero y Rendimiento:** Seguimiento de montos acumulados y técnico destacado del mes.

### 📝 Módulo de Nuevo Registro
- **Registro de Instalaciones Estándar:** Valor base asignado ($15.00 u opcionalmente modificable) con **cálculo y división equitativa automática del monto** entre la cantidad de técnicos seleccionados.
- **Asignaciones / Trabajos Especiales:** Registro detallado con *Título*, *Explicación/Descripción*, *Monto Total ($)* y desglose equitativo en tiempo real entre el personal asignado.
- **Clasificación por Región Operativa:**
  - Caracas
  - Guatire-Guarenas
  - Caucagua
  - Higuerote
  - Barlovento

### 👷 Gestión Completa de Técnicos
- Ficha detallada de personal con los siguientes campos:
  - **Identificación:** Nombre, Apellido y Cédula de Identidad (C.I.).
  - **Contacto:** Teléfono, Correo Electrónico y Dirección de Habitación.
  - **Estructura Orgánica:** Departamento, Cargo y Región Asignada.
  - **Dotación / Uniforme:** Talla de Camisa, Talla de Pantalón y Talla de Zapatos.
  - **Estatus:** Activación / Desactivación de técnicos en la plantilla.

### 📈 Reportes y Liquidación de Nómina
- **Filtros Avanzados:** Búsqueda y filtrado por rango de fechas (*Desde / Hasta*) y por *Región*.
- **Desglose Individual:** Muestra cantidad de instalaciones, asignaciones especiales y monto exacto a cobrar por cada técnico.
- **Exportación e Impresión:** Descarga de reportes consolidados en formato **CSV / Excel** e interfaz optimizada para impresión administrativa.

---

## 🛠️ Arquitectura y Tecnologías Utilizadas

- **Frontend:** HTML5, CSS3 (Tailwind CSS / Custom Styles), JavaScript ES6+ (Async/Fetch API).
- **Backend / API:** Google Apps Script (`doGet` / `doPost` en formato JSON).
- **Base de Datos:** Google Sheets (alojado en Google Drive con pestañas `Tecnicos`, `Instalaciones` y `TrabajosEspeciales`).
- **Hosting Web:** GitHub Pages (Servidor estático SSL 24/7).

---

## 🗄️ Estructura de la Base de Datos (Google Sheets)

La hoja de cálculo `MigTel_BD` cuenta con las siguientes tablas:

1. **`Tecnicos`**: `ID`, `Nombre_Apellido`, `Cedula`, `Telefono`, `Email`, `Direccion`, `Departamento`, `Cargo`, `TallaCamisa`, `TallaPantalon`, `TallaZapatos`, `Region`, `Estado`.
2. **`Instalaciones`**: `ID`, `Fecha`, `Region`, `PrecioTotal`, `TecnicosIDs`, `MontoPorTecnico`.
3. **`TrabajosEspeciales`**: `ID`, `Fecha`, `Titulo`, `Explicacion`, `Region`, `MontoTotal`, `TecnicosIDs`, `MontoPorTecnico`.

---

## 🚀 Instalación y Despliegue

### 1. Backend (Google Apps Script)
1. Abre tu hoja de cálculo `MigTel_BD` en Google Drive.
2. Ve a **Extensiones > Apps Script**.
3. Pega el código de la API (`Código.gs`) con las funciones `doGet(e)` y `doPost(e)`.
4. Haz clic en **Implementar > Nueva implementación**.
5. Selecciona el tipo **Aplicación Web**, configura *Quién tiene acceso* como **Cualquier persona** y copia la `URL de la aplicación web`.

### 2. Frontend (GitHub Pages)
1. Crea un repositorio público en GitHub llamado `migtel-app`.
2. Sube tu archivo fuente renombrándolo a `index.html` e inserta la constante de la API:
   ```javascript
   const API_URL = "https://script.google.com/macros/s/TU_SCRIPT_ID_AQUI/exec";
   ```
3. Ve a **Settings > Pages**, en *Branch* selecciona `main` / `(root)` y guarda los cambios.
4. Tu sitio web quedará activo en `https://tu-usuario.github.io/migtel-app/`.

---

## 📄 Licencia y Derechos

Desarrollado para el uso exclusivo de la empresa **MigTel**. Todos los derechos reservados.
