BINAC - Sitio Web y Panel Financiero
Este repositorio contiene el código fuente de la página de inicio de BINAC y una herramienta de panel financiero integrada. La aplicación está construida con React y utiliza Firebase para la autenticación y la base de datos en tiempo real.

✨ Características
Página de Inicio de BINAC: Un landing page moderno que presenta los servicios de BINAC.

Panel Financiero Interactivo:

Registro de ingresos y gastos.

Visualización de métricas clave: ingresos totales, gastos totales, rentabilidad neta y margen.

Gráficos para el análisis de datos mensuales y por categoría.

Gestión de transacciones (crear, editar, eliminar).

Backend con Firebase: Autenticación de usuarios y base de datos Firestore para persistencia de datos en tiempo real.

Estructura Modular: El código está organizado en componentes reutilizables para facilitar el mantenimiento y la escalabilidad.

🚀 Cómo Empezar
Sigue estos pasos para tener una copia del proyecto funcionando en tu máquina local.

Prerrequisitos
Node.js (versión 16 o superior)

npm (generalmente viene con Node.js)

Una cuenta de Firebase para configurar tu propio backend.

⚙️ Instalación y Configuración
Clona el repositorio:

git clone https://github.com/tu-usuario/binac-website.git
cd binac-website

Instala las dependencias del proyecto:

npm install

Configura las variables de entorno de Firebase:

Crea un archivo llamado .env.local en la raíz del proyecto.

Añade tus credenciales de configuración de Firebase a este archivo. Puedes encontrarlas en la configuración de tu proyecto de Firebase.

# .env.local

REACT_APP_FIREBASE_API_KEY="TU_API_KEY"
REACT_APP_FIREBASE_AUTH_DOMAIN="TU_AUTH_DOMAIN"
REACT_APP_FIREBASE_PROJECT_ID="TU_PROJECT_ID"
REACT_APP_FIREBASE_STORAGE_BUCKET="TU_STORAGE_BUCKET"
REACT_APP_FIREBASE_MESSAGING_SENDER_ID="TU_SENDER_ID"
REACT_APP_FIREBASE_APP_ID="TU_APP_ID"

Configura las reglas de seguridad de Firestore:
Para que la aplicación funcione correctamente, asegúrate de tener las siguientes reglas de seguridad en tu base de datos de Firestore:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Permite a los usuarios autenticados leer y escribir solo sus propios datos
    match /artifacts/{appId}/users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}

▶️ Ejecutar la Aplicación
Una vez que hayas instalado las dependencias y configurado las variables de entorno, puedes iniciar la aplicación:

npm start

Esto ejecutará la aplicación en modo de desarrollo. Abre http://localhost:3000 para verla en tu navegador.
