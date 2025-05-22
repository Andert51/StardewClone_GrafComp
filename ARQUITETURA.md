
---
Descripción técnica y detallada de la arquitectura del proyecto con todos los núcleos clave a implementar, para una descripción mas amigable revisar: [[Descripción del Proyecto]]
## 🌱 **RPG de Gestión de Granjas: Sistemas y Componentes Principales**

> Un desglose de los sistemas y módulos fundamentales que dan vida a la jugabilidad principal de un **RPG de granja 2D**.
> ![[Pasted image ./Arquitectura.png]]

---

### 🎬 **Gestión de Escenas**

Manejo eficiente de las distintas áreas del mundo del juego (por ejemplo, granja, pueblo, interiores de casas, cuevas). Incluye transiciones fluidas entre escenas, carga/descarga dinámica de recursos y optimización de memoria.

> Implementación de un controlador de escenas para cargar y descargar escenas a medida que el jugador se mueve entre múltiples zonas, creación de múltiples escenas para interiores y exteriores como la escena del campo y la escena de la cabaña.

---

### 🧠 **Preservación del Estado de la Escena**

Asegura que cada escena recuerde su estado anterior (por ejemplo, cultivos plantados, cofres abiertos, objetos movidos) incluso después de que el jugador salga y regrese. Se implementan sistemas de serialización e identificadores únicos de objetos para mantener la consistencia de los datos.

> Implementar funcionalidad para guardar el estado de los objetos en las escenas cuando el jugador se mueve entre ellas; creación de interfaces en C# para definir qué propiedades y métodos necesita implementar un objeto para tener su estado almacenado y restaurado.

---

### 🧱 **Propiedades de la Cuadrícula del Mapa de Baldosas (Tilemap)**

Define propiedades específicas para cada baldosa (transitable, excavable, regable, interactuable). Es crucial para la lógica del juego, colisiones e interacciones con herramientas o NPCs.

> Implementar un sistema que permita pintar propiedades como dónde puede soltarse un objeto sobre mapas de baldosas especiales para proporcionar un flujo de trabajo visual fácil de capturar diferentes propiedades del grid; creación del cursor de cuadrícula para utilizar esas propiedades y mostrar al jugador dónde puede interactuar o soltar objetos.

---

### 🛠️ **Sistema de Uso de Herramientas**

Implementa la lógica para herramientas del jugador como la azada, regadera, pico y hoz. Incluye sincronización de animaciones, retroalimentación visual, validación de baldosas y gestión de mejoras de herramientas.

> Implementación de las herramientas básicas de granja que el jugador puede usar, como la azada para excavar la tierra, la regadera para regar el suelo y la hoz para cortar hierba.

---

### ♻️ **Gestor de Objetos Reutilizables (Pool Manager)**

Administra objetos reutilizables del juego (por ejemplo, proyectiles, partículas, VFX) para optimizar el rendimiento. Reduce la sobrecarga de instanciar/destruir objetos repetidamente reutilizando los ya existentes.

> Creación de un gestor de objetos en pool que permita definir y reutilizar prefabs de objetos, implementación de clases heredadas eficientes con POO para crear nuevos objetos.

---

### 🎆 **Gestor de Efectos Visuales y Partículas**

Gestiona todos los efectos visuales como partículas de impacto de herramientas, destellos de crecimiento de cultivos, animaciones de cosecha y efectos climáticos. Aporta pulido e inmersión mediante retroalimentación visual.

> Creación de efectos de partículas para el juego y de un gestor de efectos visuales que se usará para mostrar efectos visuales durante acciones como la cosecha.

---

### 🌿 **Sistema de Mecánicas de Cultivo**

Bucle principal del juego que involucra plantar, crecer, regar y cosechar cultivos. Es la sección central del juego que implementa una amplia gama de funcionalidades. Características:

- Etapas de crecimiento y visuales
    
- Tipos de cultivos estacionales
    
- Efectos de riego y fertilizantes
    
- Crecimiento basado en el tiempo y calendario del juego
    

> Implementación del sistema principal para plantar, crecer y cosechar cultivos, creación de clases para representar cultivos y almacenar sus datos, funcionalidad para plantar semillas en el suelo y luego cosechar los cultivos cuando estén completamente desarrollados siguiendo el sistema de tiempo; también funcionalidad para almacenar cultivos.  
> Implementación de mecánicas de juego para plantar, crecer y talar árboles usando la herramienta hacha.  
> Implementación de mecánicas que permiten a ciertos cultivos transformarse en otros cuando son cosechados, por ejemplo, un árbol talado que se convierte en un tronco que también puede cortarse; implementación de rocas como "cultivos" que pueden cosecharse con el pico.

---

### ⏸️ **Menú de Pausa**

Presenta un menú de pausa limpio y responsivo con opciones para:

- Reanudar
    
- Guardar y Cargar
    
- Configuración
    
- Salir al Menú Principal
    

> 🧪 _[Insertar captura de pantalla del UI del menú de pausa]_

> Implementación de un menú de pausa que incluye una pantalla de gestión completa del inventario y opciones rápidas del juego.

---

### 💾 **Sistema de Guardado**

Guarda todo el estado del juego, incluyendo:

- Progreso del jugador
    
- Inventario y objetos
    
- Relaciones con NPCs
    
- Cambios en el mundo (por ejemplo, crecimiento de cultivos, estados de escenas)
    

Utiliza serialización (por ejemplo, JSON, ScriptableObjects o archivos binarios).

> Implementar todo lo necesario para guardar el juego en un archivo en disco y cargarlo nuevamente usando interfaces en C# que definan todas las propiedades y métodos que un objeto necesita tener para poder guardar su estado; uso de serialización binaria en C# para convertir todos los datos de clases a un archivo en disco y deserialización para cargarlo de nuevo.  
> Esta es una implementación compleja y podría tener su propio proyecto aparte.

---

### 🎨 **Personalización del Jugador**

Permite a los jugadores personalizar su personaje con:

- Apariencia (cabello, tono de piel, ropa)
    
- Nombre, género y cumpleaños
    
- Futuras expansiones pueden incluir personalización del hogar/granja
    

> Implementación de un sistema completo de personalización del jugador que permite personalizar el personaje, camisa, pantalones, peinado, color de piel, sombreros y adornos como gafas.

---

### 🧭 **Sistema de Pathfinding para NPCs**

Implementa algoritmos (como **Dijkstra** o **A***), permitiendo:

- Comportamiento programado de NPCs
    
- Navegación con obstáculos
    
- Cambios dinámicos de ruta según la hora o eventos
    

> 🤖 _[Incluir diagrama de la cuadrícula de pathfinding si se desea]_

> Implementación de mecánicas de pathfinding con el algoritmo A*, mecánicas para NPCs y rutinas basadas en el tiempo para los personajes no jugables.

---

### 🎵 **Sistema de Efectos de Sonido y Música**

Sistema de audio modular para:

- Reproducir sonidos ambientales (viento, pasos, animales)
    
- Disparar sonidos de acciones (uso de herramientas, cosecha, interfaz)
    
- Gestionar pistas de música de fondo según la escena, hora o estación
    

Utiliza el **Audio Mixer de Unity** y reutilización de **AudioSource**.

> Implementación de todo lo relacionado con audio: mezclador de sonido, sonidos de pasos del jugador, sonidos de acciones, gestión de audio, sonidos ambientales y música.

---

### 🎮 **Controlador Central del Jugador**

Gestiona el movimiento del jugador, animación, entrada, interacciones y uso de herramientas. Se conecta con otros sistemas como el tiempo, cultivos y eventos para formar una experiencia de juego unificada.

> Creación del objeto jugador con jerarquía, creación de una clase abstracta con patrón Singleton que se usará para los componentes del jugador y otros gestores del juego, implementación del movimiento del jugador usando eventos, además de la creación de animaciones del jugador usando componentes animados y controladores de animación con el sistema Animator.

---

### 🗺️ **Escenas del Juego y Tilemaps**

Mapas del mundo estructurados compuestos por **Tilemaps** en capas:

- Suelo, edificios, decoraciones
    
- Capas de colisión, interacción e iluminación
    
- Cambios estacionales/ambientales en las baldosas
    

Cada escena tiene su propia lógica pero sigue un sistema compartido de cuadrícula.

> Creación de una jerarquía de Tilemaps para escenas del juego, creación de una escena de patio de granja con baldosas de colisión e implementación de una funcionalidad de cámara dinámica para mantener la cámara dentro de los límites del área visible; creación de un desvanecedor de escenario para oscurecer elementos cuando el jugador pasa detrás de ellos.

---

### 🎒 **Sistema de Inventario y Objetos (UI)**

Sistema de UI intuitivo y expandible para:

- Ranuras de objetos con arrastrar y soltar
    
- Selección rápida de herramientas
    
- Descripciones de objetos, tamaños de pila y estados de usabilidad
    

Incluye mecánicas para recoger, usar, descartar y vender objetos.

> Creación de clases necesarias para representar objetos, estructuras de datos para almacenar listas de objetos, creación de prefabs para agregar objetos a la escena, creación de un gestor de inventario con funcionalidad básica para la gestión de objetos e inventario, creación de atributos personalizados de propiedades con POO para mejorar el flujo de trabajo.  
> Implementación de una burbuja de inventario personalizada para mostrar qué objetos tiene el jugador y la funcionalidad para añadir, recoger, soltar, reordenar y seleccionar objetos en la barra de inventario.

---

### 🕒 **Sistema de Tiempo del Juego**

Un sistema de reloj en tiempo real o semi-real que:

- Impulsa el crecimiento de cultivos y las rutinas de los NPCs
    
- Gestiona eventos (festivales, horarios de tiendas)
    
- Incluye días, estaciones y ciclos anuales
    
- Se representa visualmente con un **reloj en el HUD**
    

> Implementación de un sistema en tiempo semi-real de juego que genera eventos relacionados con el tiempo y la funcionalidad de una interfaz gráfica que muestra el reloj del juego y se muestra en la parte superior del HUD.

---