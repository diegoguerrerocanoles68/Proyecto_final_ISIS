# Prototipo en Figma – P1 Plataforma de autoaprendizaje digital (CLENA)
 
## Enlace
 
**Prototipo navegable:** https://www.figma.com/design/xvF5UTqaPJvXtr6rebz77J/Dise%C3%B1o-para-el-CLENA?node-id=0-1&t=KUKVDfvTY4BlVY87-1
 
El archivo está compartido con el equipo de Backend y con djromero@uninorte.edu.co, con permiso de comentario.
 
## Resumen
 
- **10 pantallas**, cada una nombrada con la historia de usuario que cubre.
- **8 pantallas de celular** (412 × 917 px) para el público: visitantes y usuarios mayores.
- **2 pantallas de computador** (1440 × 900 px) para el personal del CLENA.
- **Dos flujos navegables** en modo Prototype: uno para el público y otro para el personal.
## Accesibilidad aplicada
 
Pensado para el público real de la Sala de Internet (adultos mayores y personas con poca experiencia digital):
 
- Letra de mínimo 18 px (el enunciado exige 16 px).
- Botones grandes, con esquinas redondeadas y texto claro.
- Texto oscuro sobre fondo claro para un buen contraste, y botones azul oscuro con texto blanco.
- Botones **Ayuda**, **A-** y **A+** visibles arriba en cada pantalla del público (HU-28 y HU-36).
- Cada campo de formulario con su etiqueta visible.
- El color nunca es la única señal: la respuesta correcta lleva ícono ✓ y texto (HU-21).
## Pantallas
 
### Pantallas de celular (público)
 
**1. HU-45 Entrada por QR**
Pantalla de bienvenida a la que se llega al escanear el código QR del puesto, sin necesidad de iniciar sesión. Muestra el título «Bienvenido al CLENA» y el botón «Empezar».
 
![HU-45 Entrada por QR](capturas/hu-45.png)
 
**2. HU-09 Inicio y categorías**
Pantalla de inicio con la categoría «Phishing» como botón grande con ícono y texto, y la opción de crear cuenta.
 
![HU-09 Inicio y categorías](capturas/hu-09.png)
 
**3. HU-10 Guía paso a paso**
Muestra un paso a la vez («Paso 2 de 6»), con instrucción corta, imagen de apoyo y botones grandes «Anterior» y «Siguiente».
 
![HU-10 Guía paso a paso](capturas/hu-10.png)
 
**4. HU-21 Pregunta con retroalimentación**
Pregunta de práctica («Pregunta 2 de 4») con opciones grandes. Muestra la retroalimentación de acierto con ícono ✓, texto y una explicación corta, y el botón «Continuar».
 
![HU-21 Pregunta con retroalimentación](capturas/hu-21.png)
 
**5. HU-28 Menú de Ayuda**
Menú que se abre desde el botón «Ayuda» de cualquier pantalla, con tres opciones: «Preguntas frecuentes», «¿Qué significa esta palabra?» y «Llamar a un monitor».
 
![HU-28 Menú de Ayuda](capturas/hu-28.png)
 
**6. HU-29 Solicitar ayuda presencial**
Formulario con el número de equipo y el tema de la duda. Al enviar, muestra «Un monitor vendrá pronto» y la posición en la cola, con opción de cancelar.
 
![HU-29 Solicitar ayuda presencial](capturas/hu-29.png)
 
**7. HU-01 Registro con consentimiento**
Formulario con nombre, número de identificación, fecha de nacimiento, teléfono o correo, y la casilla de aceptación del aviso de privacidad.
 
![HU-01 Registro con consentimiento](capturas/hu-01.png)
 
**8. HU-23 Mi progreso**
Muestra cada guía con su barra de progreso y porcentaje. Las completadas llevan una marca y las pendientes, el botón «Empezar».
 
![HU-23 Mi progreso](capturas/hu-23.png)
 
### Pantallas de computador (personal del CLENA)
 
**9. HU-30 Cola de solicitudes (monitor)**
Tabla con las solicitudes de ayuda: equipo, tema, guía y paso, y tiempo de espera, de la más antigua a la más reciente. Incluye los botones «Tomar» y «Resolver».
<img width="921" height="684" alt="image" src="https://github.com/user-attachments/assets/54a9d709-0348-4818-8efc-1e34d41996cd" />

 
![HU-30 Cola de solicitudes](capturas/hu-30.png)
 
**10. HU-31 Panel de temas más consultados**
Panel para la coordinadora con el top de guías más abiertas, un gráfico de consultas, el filtro de fechas y el resumen de solicitudes de ayuda.
 
![HU-31 Panel de temas más consultados](capturas/hu-31.png)
 
## Flujos navegables
 
**Flujo principal (público):**
HU-45 Entrada por QR → HU-09 Inicio y categorías → HU-10 Guía paso a paso → HU-21 Pregunta con retroalimentación → HU-23 Mi progreso.
 
**Flujo de ayuda (desde cualquier pantalla del público):**
Botón «Ayuda» → HU-28 Menú de Ayuda → «Llamar a un monitor» → HU-29 Solicitar ayuda presencial.
 
**Flujo de registro:**
HU-09 Inicio y categorías → «Crear cuenta» → HU-01 Registro con consentimiento → HU-23 Mi progreso.
 
**Flujo del personal (computador):**
HU-30 Cola de solicitudes ↔ HU-31 Panel de temas más consultados.
 
## Comparación con la aplicación construida por Backend
 
**Pantalla comparada:** PENDIENTE (por ejemplo, HU-09 Inicio y categorías).
 
| Aspecto | Prototipo en Figma | Aplicación de Backend |
|---|---|---|
| Tamaño de la letra | PENDIENTE | PENDIENTE |
| Tamaño de los botones | PENDIENTE | PENDIENTE |
| Contraste y colores | PENDIENTE | PENDIENTE |
| Botones de ayuda y tamaño de letra | PENDIENTE | PENDIENTE |
 
**Diferencias que deben corregirse:** PENDIENTE.
 
![Pantalla del prototipo](capturas/comparacion-figma.png)
![Pantalla de la aplicación de Backend](capturas/comparacion-backend.png)
 
## Nota
 
El prototipo es una guía para el equipo de Backend, no un diseño final. Los textos, imágenes y datos de ejemplo son ficticios.
 
