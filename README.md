# Cashflow App

Una aplicación simple de **cashflow** que permite registrar y visualizar ingresos y gastos. La aplicación cuenta con un modal para facilitar el registro de nuevas transacciones de manera rápida y sencilla.

## Características

- Registro de **ingresos** y **gastos**.
- Visualización de un resumen de las transacciones.
- Modal interactivo para añadir nuevas transacciones.
- Totalización automática de ingresos y gastos.
- Interfaz amigable, utilizando **Vue.js** y **Tailwind CSS**.

## Tecnologías

- **Vue.js 3** - Framework de JavaScript para la interfaz de usuario.
- **Tailwind CSS** - Framework de CSS utilitario para diseño rápido y responsivo.

## Instalación

Sigue los siguientes pasos para instalar y ejecutar la aplicación en tu entorno local.

1. Clona el repositorio:

   ```bash
   git clone https://github.com/lexand-dev/cashFlow.git
   ```

2. Navega a la carpeta del proyecto:

   ```bash
   cd cashFlow
   ```

3. Instala las dependencias necesarias:

   ```bash
   npm install
   ```

4. Inicia la aplicación:

   ```bash
   npm run dev
   ```

## Uso

1. Al iniciar la aplicación, se muestra un resumen de tus **ingresos** y **gastos** actuales.
2. Haz clic en el botón **Añadir transacción** para abrir el modal.
3. En el modal, puedes ingresar el **título**, la **descripción**, el **monto** y seleccionar si la transacción es un **ingreso** o un **gasto**.
4. Las transacciones ingresadas se reflejarán en el resumen de forma automática.
5. Puedes ver el balance actualizado basado en las transacciones registradas.

## Estructura del Proyecto

```bash
├── public
├── src
│   ├── assets
│   ├── components
│   │   ├── Action.vue
│   │   ├── Graphic.vue
│   │   ├── Header.vue
│   │   ├── Home.vue
│   │   ├── Layout.vue
│   │   ├── Modal.vue
│   │   ├── Movement.vue
│   │   ├── Movements.vue
│   │   ├── Resume.vue
│   │   ├── SplashScreen.vue
│   ├── App.vue
│   ├── main.js
│   └── style.css
```
