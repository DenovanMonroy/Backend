# Task Manager App

## Descripción del Proyecto

Esta es una aplicación móvil desarrollada en Android Studio utilizando Kotlin y Jetpack Compose para la gestión de tareas básicas con operaciones CRUD (Crear, Leer, Actualizar, Eliminar). La aplicación se conecta a una API REST utilizando Retrofit y permite a los usuarios visualizar una lista de tareas, agregar nuevas tareas, editarlas y eliminarlas.

El objetivo principal de este proyecto es proporcionar una interfaz sencilla e intuitiva para administrar tareas de manera eficiente. Se ha implementado el patrón de arquitectura MVVM (Model-View-ViewModel) para mantener una estructura de código limpia y escalable.

---

## Instrucciones para Ejecutar el Proyecto

### **1. Requisitos Previos**
- Android Studio instalado (versión más reciente recomendada).
- Emulador de Android o un dispositivo físico con depuración USB habilitada.
- Servidor backend con una API REST disponible en `http://10.0.2.2:3000/api/` (para pruebas locales, se puede usar JSON Server o un backend propio).

### **2. Clonar el Repositorio**
```sh
  git clone https://github.com/tu-DenovanMonroy/task-manager-app.git
  cd task-manager-app
```

### **3. Configurar el Servidor Backend **
El servidor se encuentra en la carpeta con el mismo nombre y para poder se tienen que ejecutar los siguientes codigos en la terminal:
```sh
  npm install 
  npm run dev
```

### **4. Abrir el Proyecto en Android Studio**
1. Iniciar Android Studio.
2. Seleccionar **Open an Existing Project**.
3. Buscar la carpeta clonada y abrirla.
4. Esperar a que Android Studio sincronice las dependencias.

### **5. Ejecutar la Aplicación**
- Seleccionar un dispositivo/emulador en Android Studio.
- Hacer clic en **Run** (o presionar `Shift + F10`).

---

## Arquitectura de la Aplicación

La aplicación sigue el patrón **MVVM (Model-View-ViewModel)** para separar la lógica de negocio de la interfaz de usuario y facilitar el mantenimiento y escalabilidad.

### **1. Model (Modelo)**
Define los datos que se utilizan en la aplicación. En este caso, la clase `Task.kt` representa una tarea con `id`, `title`, `description` y `date`.

### **2. ViewModel (Lógica de Negocio)**
La clase `TaskViewModel.kt` maneja la lógica de la aplicación y usa `StateFlow` para actualizar la UI de forma reactiva. Se encarga de comunicarse con el repositorio para obtener y manipular los datos.

### **3. Repository (Repositorio)**
`TaskRepository.kt` actúa como una capa intermedia entre `TaskApi.kt` y el ViewModel. Permite encapsular la lógica de acceso a datos.

### **4. API (Interfaz de Red)**
`TaskApi.kt` define las operaciones REST utilizando Retrofit para interactuar con un backend.

### **5. UI (Interfaz de Usuario)**
La UI se basa en **Jetpack Compose**:
- `TaskListScreen.kt`: Muestra la lista de tareas usando `LazyColumn`.
- `TaskItem.kt`: Define el diseño individual de cada tarea.
- `MainActivity.kt`: Punto de entrada de la aplicación, donde se inicializa el ViewModel y se renderiza la UI.

---

## Desafíos Encontrados y Soluciones

### **1. Integración con Retrofit**
**Problema:** Inicialmente, la aplicación no podía conectarse al backend en el emulador.
**Solución:** Se utilizó `http://10.0.2.2:3000/api/` en lugar de `localhost`, ya que `10.0.2.2` es la dirección para acceder al host desde el emulador.

### **2. Manejo de Estado en la UI**
**Problema:** La lista de tareas no se actualizaba en tiempo real después de realizar cambios.
**Solución:** Se utilizó `StateFlow` en `TaskViewModel.kt` para gestionar el estado de las tareas y garantizar que la UI se reactive correctamente cuando los datos cambian.

### **3. Optimización del Diseño con Jetpack Compose**
**Problema:** La UI no estaba optimizada y las tareas se veían desordenadas.
**Solución:** Se utilizó `LazyColumn` para listas eficientes y `Card` de Material 3 para mejorar la visualización de cada tarea.

---

## Dependencias Utilizadas

| Dependencia | Propósito |
|-------------|----------|
| `androidx.lifecycle:lifecycle-viewmodel-ktx` | Manejo del ciclo de vida y ViewModel |
| `androidx.lifecycle:lifecycle-runtime-ktx` | Uso de corrutinas en ViewModel |
| `androidx.compose.ui:ui` | Jetpack Compose para UI declarativa |
| `androidx.compose.material3:material3` | Implementación de Material 3 |
| `com.squareup.retrofit2:retrofit` | Cliente HTTP para la API REST |
| `com.squareup.retrofit2:converter-gson` | Conversión JSON ↔ Kotlin usando Gson |
| `com.squareup.okhttp3:logging-interceptor` | Registro de solicitudes y respuestas HTTP |
| `org.jetbrains.kotlinx:kotlinx-coroutines-core` | Uso de corrutinas para llamadas asíncronas |

---

