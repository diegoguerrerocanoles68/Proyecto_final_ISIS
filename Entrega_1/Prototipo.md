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
 
<img width="283" height="577" alt="image" src="https://github.com/user-attachments/assets/1ffe0a18-f81e-4616-9a8a-c3a50bcb39b3" />

 
**2. HU-09 Inicio y categorías**
Pantalla de inicio con la categoría «Phishing» como botón grande con ícono y texto, y la opción de crear cuenta.
 
<img width="269" height="574" alt="image" src="https://github.com/user-attachments/assets/521cf504-ebd1-425c-b1bb-3455aae1e401" />

 
**3. HU-10 Guía paso a paso**
Muestra un paso a la vez («Paso 2 de 6»), con instrucción corta, imagen de apoyo y botones grandes «Anterior» y «Siguiente».
 
<img width="273" height="572" alt="image" src="https://github.com/user-attachments/assets/43da355f-e164-41e4-9de1-3f9333d5a2c6" />

 
**4. HU-21 Pregunta con retroalimentación**
Pregunta de práctica («Pregunta 2 de 4») con opciones grandes. Muestra la retroalimentación de acierto con ícono ✓, texto y una explicación corta, y el botón «Continuar».
 
<img width="271" height="574" alt="image" src="https://github.com/user-attachments/assets/364b86c1-f014-4b70-9eb5-ce73de9b2a26" />

 
**5. HU-28 Menú de Ayuda**
Menú que se abre desde el botón «Ayuda» de cualquier pantalla, con tres opciones: «Preguntas frecuentes», «¿Qué significa esta palabra?» y «Llamar a un monitor».
 
<img width="270" height="578" alt="image" src="https://github.com/user-attachments/assets/5b117edc-4717-4008-9b67-6ab67090d612" />

 
**6. HU-29 Solicitar ayuda presencial**
Formulario con el número de equipo y el tema de la duda. Al enviar, muestra «Un monitor vendrá pronto» y la posición en la cola, con opción de cancelar.
 
<img width="266" height="566" alt="image" src="https://github.com/user-attachments/assets/572bb832-f585-494c-9a27-fc1582e0c3b5" />

 
**7. HU-01 Registro con consentimiento**
Formulario con nombre, número de identificación, fecha de nacimiento, teléfono o correo, y la casilla de aceptación del aviso de privacidad.
 
<img width="278" height="571" alt="image" src="https://github.com/user-attachments/assets/4d63355a-80b2-4511-bf15-af1469af7dd6" />

 
**8. HU-23 Mi progreso**
Muestra cada guía con su barra de progreso y porcentaje. Las completadas llevan una marca y las pendientes, el botón «Empezar».
 
<img width="274" height="567" alt="image" src="https://github.com/user-attachments/assets/52b0816a-1967-4dbc-90a1-d6adf42cc77e" />

 
### Pantallas de computador (personal del CLENA)
 
**9. HU-30 Cola de solicitudes (monitor)**
Tabla con las solicitudes de ayuda: equipo, tema, guía y paso, y tiempo de espera, de la más antigua a la más reciente. Incluye los botones «Tomar» y «Resolver».
<img width="921" height="684" alt="image" src="https://github.com/user-attachments/assets/54a9d709-0348-4818-8efc-1e34d41996cd" />

 
 
**10. HU-31 Panel de temas más consultados**
Panel para la coordinadora con el top de guías más abiertas, un gráfico de consultas, el filtro de fechas y el resumen de solicitudes de ayuda.
 
<img width="966" height="629" alt="image" src="https://github.com/user-attachments/assets/7cfc5e0e-27b9-47a5-bd35-8822f9a528ad" />

 
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
 
**Pantalla comparada:** HU-09 Inicio y categorías (nuestro Figma) frente a la pantalla de inicio «Explorar guías» de la versión de prueba de Backend, llamada **Kamá**: https://claude.ai/artifact/VN5Na3MUrkuJhcniSfyqqx
 
Revisamos la pantalla de inicio de la versión de prueba en un ancho de celular (412 px).

 <img width="269" height="574" alt="image" src="https://github.com/user-attachments/assets/521cf504-ebd1-425c-b1bb-3455aae1e401" />
<img width="412" height="2055" alt="image" src="https://github.com/user-attachments/assets/29210ab2-e0a1-4030-93e6-a345d949264e" />

| Aspecto | Prototipo en Figma | Aplicación de Backend |
|---|---|---|
| Tamaño de la letra | Mínimo 18 px. Algunos textos de apoyo son más pequeños que los títulos | Texto base de 20 px y selector de tres tamaños de letra (normal, grande y muy grande) |
| Botones | Botones grandes de color azul con texto blanco | Botones de 52 a 64 px de alto y tarjetas de tema de más de 120 px, fáciles de tocar |
| Ayuda | Botón «Ayuda» en la parte superior, junto a «A-» y «A+» | Botón «Pedir ayuda a una persona» en la parte superior, con texto completo |
| Accesibilidad | Tamaño de letra con «A-» y «A+» | Selector de letra, «Alto contraste», «Leer en voz alta» y «Modo sencillo» |
| Temas | Una categoría: «Phishing» | Cinco temas por tipo de engaño: correos, SMS y WhatsApp, llamadas, engaños a la medida y códigos QR |
| Crear cuenta | Enlace «Crear cuenta» en el inicio | No se ve en la pantalla de inicio |
 
**Lo que coincide con el diseño:** la ayuda siempre visible arriba, botones grandes, texto sencillo, colores azules con buen contraste y un tema por botón con ícono y texto.
 
**Lo que la aplicación hace mejor que nuestro diseño:** la pregunta inicial «¿cómo ve mejor la pantalla?», que deja elegir letra grande o alto contraste desde el primer momento, y los títulos de cada tema, que dicen el tipo de engaño con palabras sencillas («Correos falsos», «Llamadas falsas»).
 
**Diferencias que conviene revisar con el equipo de Backend (para el siguiente sprint):**
1. **Crear cuenta (HU-01 y HU-03):** en nuestro diseño hay una invitación opcional a crear cuenta desde el inicio. Esperamos ver ese acceso para guardar el progreso.
2. **Temas (HU-17 a HU-20):** el backlog define la categoría «Phishing» con las guías de Smishing, Vishing, Quishing y Falso soporte técnico. La aplicación muestra «Engaños hechos a su medida» (spear phishing) y no muestra «Falso soporte técnico». Conviene confirmar el alcance con el Product Owner.
3. **Quishing:** aparece como «Próximamente». Es una historia «Must» (HU-19) y debería estar disponible.
4. **Textos pequeños de nuestro Figma:** algunos textos de apoyo, como «Explora y aprende» y «Crear cuenta», se ven más pequeños que el resto. Los vamos a subir a 18 px para igualar la legibilidad de la aplicación.
Solo comparamos la pantalla de inicio. Las demás pantallas las revisaremos cuando estén en la versión de prueba.
  Backend, no un diseño final. Los textos, imágenes y datos de ejemplo son ficticios.
 
