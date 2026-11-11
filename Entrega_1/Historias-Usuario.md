# Historias de usuario – P1 Plataforma de autoaprendizaje digital (CLENA)
 
Historias registradas como Issues con la etiqueta `historia-usuario` en el repositorio del equipo de Backend. Los puntos los estima el equipo de Backend. Prioridad según MoSCoW (Must, Should, Could, Won't).
 
Las historias con autor individual fueron escritas por ese integrante. Las demás fueron pensadas y trabajadas en conjunto con el equipo de octavo semestre.
 
## Historias por autor
 
- **Yussef Kassem Issa:** HU-12, HU-23, HU-34, HU-41, HU-44
- **Sair Javid Cervantes Rey:** HU-17, HU-27, HU-28, HU-37, HU-42
- **Diego Guerrero Canoles:** HU-11, HU-33, HU-35, HU-36, HU-40
- **Andrés Camilo Badillo Cervera:** HU-09, HU-10, HU-13, HU-43
- **En conjunto con Backend:** las demás historias del listado.
---
 
### HU-01 · Registro con consentimiento
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** visitante de la Sala de Internet **quiero** crear una cuenta con mi nombre **para** guardar mi progreso entre visitas.
 
Prioridad: Must · Puntos: 5  · Sprint 1
 
Criterios de aceptación:
 
- Dado que estoy en la pantalla de registro, deberé ingresar mi nombre, número de identificación, fecha de nacimiento, teléfono y/o correo, y aceptando las políticas de privacidad, entonces se crea mi cuenta con rol de usuario público y queda con la sesión iniciada.
- Dado que no marcó la casilla de consentimiento, cuando intento registrarme, entonces el sistema no crea la cuenta y me explica que debo aceptar el aviso.
- Dado que el teléfono ya está registrado en otra cuenta, cuando intento registrarme con él, entonces veo el mensaje “Ese teléfono ya está en uso, prueba con otro”.
- Dado que el correo ya está registrado en otra cuenta, cuando intento registrarme con él, entonces veo el mensaje “Ese correo ya está en uso, prueba con otro”.
- Dado que mi número de identificación está registrado, cuando intento registrarme con él, entonces veo el mensaje “Este usuario ya tiene una cuenta”.
- Se le enviará al usuario un código a su correo o a su teléfono para validar y poder registrarse.
Notas: el aviso de privacidad debe decir qué datos se guardan, para qué y cómo eliminarlos. Se guarda la fecha y la versión del aviso aceptado.
 
 
---
 
### HU-02 · Inicio de sesión con sesión persistente
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario registrado **quiero** iniciar sesión con mi identificación con teléfono o correo **para** continuar con mis guías y actividades.
 
Prioridad: Must · Puntos: 3 · Sprint 1
 
Criterios de aceptación:
 
- Dado que ingreso correctamente mi número de identificación junto mi correo o mi teléfono, entonces recibo un código a mi correo o a mi teléfono y lo digito en la plataforma para poder entrar a mi página de inicio.
- Dado que mis datos son incorrectos, cuando inicio sesión, entonces veo «Credenciales inválidas», sin indicar cuál de los dos falló.
- Dado que inicié sesión, recibo un access token y refresh token, si mi access token venció, cuando sigo usando la aplicación, entonces se renueva con el refresh token sin sacarme de lo que estaba haciendo.
- Dado que presiono «Cerrar sesión», entonces el refresh token se invalida y vuelvo a la pantalla de inicio.
- Dado que intento entrar a una ruta que mi rol no permite, entonces el backend responde 403 y el frontend me lleva a una página con un mensaje claro.
Notas: los computadores de la sala son compartidos. Considerar cierre de sesión automático tras un periodo de inactividad (por ejemplo, 15 minutos). El refresh token se guarda con hash en la base de datos y se rota en cada uso; /auth/login y /auth/refresh tienen límite de intentos con @nestjs/throttler (ver el spike técnico del Sprint 1).
 
 
---
 
### HU-03 · Usar la plataforma sin cuenta
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** visitante que llega por primera vez **quiero** leer las guías sin tener que registrarme **para** empezar a aprender de inmediato.
 
Prioridad: Must · Puntos: 2  · Sprint 1
 
Criterios de aceptación:
 
- Dado que no he iniciado sesión, cuando abro la plataforma, entonces puedo ver categorías, guías y la ayuda.
- Dado que no he iniciado sesión, cuando termino una actividad, entonces veo mi resultado y una invitación opcional a crear cuenta para guardar el progreso.
- Dado que no he iniciado sesión, cuando intento una acción que requiere cuenta, entonces veo una invitación a registrarse sin perder lo que estaba haciendo. (La ayuda presencial sin cuenta se cubre en HU-29.)
---
 
### HU-04 · Gestión de cuentas del personal
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** administrador **quiero** crear, editar y desactivar cuentas del personal del CLENA **para** controlar quién puede modificar el contenido y atender solicitudes.
 
Prioridad: Must · Puntos: 5 · Sprint 1
 
Criterios de aceptación:
 
- Dado que soy administrador, cuando creo una cuenta con nombre, correo y contraseña temporal, entonces la cuenta queda activa.
- Dado que un monitor deja de trabajar en el CLENA, cuando desactivo su cuenta, entonces ya no puede iniciar sesión, pero sus registros históricos se conservan.
- Dado que una cuenta tiene contraseña temporal, cuando su dueño inicia sesión por primera vez, entonces el sistema le pide cambiarla verificando su identidad con un mensaje a su correo electrónico.
- Dado que no soy administrador, cuando intento acceder a esta gestión, entonces el sistema lo impide.
- El script de semillas crea un administrador inicial con credenciales tomadas de variables de entorno.
---
 
### HU-05 · Eliminar mi cuenta
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario registrado **quiero** eliminar mi cuenta y mis datos **para** ejercer mi derecho de supresión.
 
Prioridad: Must · Puntos: 3  · Sprint 1
 
Criterios de aceptación:
 
- Dado que estoy en mi perfil, cuando elijo «Eliminar mi cuenta», entonces el sistema me explica qué se borrará y me pide confirmar con correo o mi teléfono
- Dado que confirmo, entonces se borran mis datos personales y mi progreso, y se cierra mi sesión.
- Las estadísticas agregadas (por ejemplo, cuántas veces se consultó una guía) se conservan sin datos que me identifiquen.
Notas: la eliminación se ejecuta en una transacción. Para el progreso y los intentos se usa onDelete: Cascade; para los registros que alimentan estadísticas (consultas de guías, solicitudes de ayuda) se anonimiza la referencia al usuario. La decisión se justifica en el PR de la migración y en el documento de tratamiento de datos.
 
 
---
 
### HU-06 · Iniciar sesión como personal del CLENA
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** personal del CLENA **quiero** poder iniciar sesión con mi correo y contraseña **para** administrar la plataforma
 
Prioridad: Must · Puntos: 3 · Sprint 1
 
Criterios de aceptación:
 
- Dado que registre correctamente mi correo y contraseña ya creados, se me enviará un código de verificación al correo para poder iniciar sesión
- Dado que registré incorrectamente mi correo o mi contraseña, se me mostrará un mensaje diciendo: “Credenciales incorrectas”
---
 
### HU-07 · Restablecimiento de contraseña para personal del CLENA
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** personal del CLENA que olvidó su contraseña y tengo el correo **quiero** poder restablecer mi contraseña **para** no perder mi cuenta.
 
Prioridad: Should· Puntos: 2
 
Criterios de aceptación:
 
- Dado que tengo un correo asociado, me llegará un correo con un código único que verifique mi identidad y en la plataforma se me habilitará la opción de poder cambiar la contraseña.
---
 
### HU-08 · Perfil y preferencias
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario registrado **quiero** guardar mis preferencias de tamaño de letra, contraste y nivel de experiencia **para** no tener que configurarlas en cada visita.
 
Prioridad: Should · Puntos: 2
 
Criterios de aceptación:
 
- Dado que cambio mis preferencias, cuando cierro sesión y vuelvo a entrar desde otro computador, entonces se aplican automáticamente.
- Dado que estoy en mi perfil, entonces puedo editar mi nombre y mi correo opcional.
---
 
### HU-09 · Explorar guías por categoría
 
**Autor:** Andrés Camilo Badillo Cervera
 
**Como** visitante con poca experiencia digital **quiero** ver las guías organizadas por categoría con íconos y nombres claros **para** encontrar rápido lo que necesito aprender.
 
Prioridad: Must · Puntos: 3  · Sprint 1
 
Criterios de aceptación:
 
- Dado que abro la plataforma, entonces la página de inicio muestra las categorías como botones grandes con ícono y texto.
- Dado que elijo una categoría, entonces veo sus guías publicadas con título, nivel y duración estimada.
- Dado que una categoría no tiene guías publicadas, entonces se muestra el mensaje «Pronto habrá guías en esta sección» en lugar de una pantalla vacía.
---
 
### HU-10 · Seguir una guía paso a paso
 
**Autor:** Andrés Camilo Badillo Cervera
 
**Como** adulto mayor **quiero** ver una guía con un paso a la vez, con texto corto e imágen **para** seguir las instrucciones sin perderme.
 
Prioridad: Must · Puntos: 5  · Sprint 1
 
Criterios de aceptación:
 
- Dado que abro una guía, entonces veo primero su objetivo («Al terminar sabrás...») y el número total de pasos.
- Dado que estoy en un paso, entonces veo su número («Paso 2 de 6»), una instrucción de máximo tres oraciones y, si existe, una imagen con texto alternativo.
- Dado que estoy en un paso, entonces tengo botones grandes «Anterior» y «Siguiente», y puedo usarlos también con el teclado.
- Dado que llego al último paso, entonces veo un mensaje de felicitación y la invitación a practicar con la actividad de la guía, si tiene una.
- Cada apertura de una guía queda registrada para las estadísticas del panel (HU-31), sin datos personales si el usuario no inició sesión.
---
 
### HU-11 · Buscar guías por palabra
 
**Autor:** Diego Guerrero Canoles
 
*Historia propia de Diego: instructivo sobre filtros de búsqueda (palabras clave).*
 
**Como** visitante **quiero** escribir lo que quiero hacer, por ejemplo «mandar foto», **para** encontrar la guía sin recorrer todas las categorías.
 
Prioridad: Should · Puntos: 3 
 
Criterios de aceptación:
 
- Dado que escribo una palabra, cuando busco, entonces veo las guías cuyo título, descripción o palabras clave la contienen.
- Dado que escribo con errores de tilde o mayúsculas («correo electronico»), entonces la búsqueda encuentra igual los resultados.
- Dado que no hay resultados, entonces veo sugerencias de categorías y la opción de pedir ayuda presencial.
Notas: usar búsqueda de texto de PostgreSQL con unaccent e índice en las columnas de búsqueda, como exige el enunciado. Prisma no crea extensiones ni índices de expresión de forma declarativa, así que la extensión y el índice GIN se crean en una migración SQL escrita a mano, y la consulta con $queryRaw queda aislada dentro del repositorio de infraestructura.
 
 
---
 
### HU-12 · Filtrar guías por nivel
 
**Autor:** Yussef Kassem Issa
 
*Historia propia de Yussef: «ver los módulos organizados por nivel (básico, intermedio, avanzado)».*
 
**Como** usuario nuevo **quiero** filtrar las guías por nivel básico, intermedio o avanzado **para** empezar por las que corresponden a mi experiencia.
 
Prioridad: Should · Puntos: 2 
 
Criterios de aceptación:
 
- Dado que estoy en una categoría, cuando elijo un nivel, entonces solo veo las guías de ese nivel.
- Dado que tengo un nivel guardado en mi perfil (HU-08), entonces ese filtro viene aplicado por defecto y puedo quitarlo.
---
 
### HU-13 · Crear y editar guías
 
**Autor:** Andrés Camilo Badillo Cervera
 
**Como** personal del CLENA **quiero** crear y editar guías con sus pasos desde un formulario **para** mantener el contenido actualizado sin depender de programadores.
 
Prioridad: Must · Puntos: 8 · Sprint 2
 
Criterios de aceptación:
 
- Dado que soy personal, cuando creo una guía, entonces ingreso título, objetivo, categoría, nivel, duración estimada y palabras clave.
- Dado que edito una guía, entonces puedo agregar, editar y eliminar pasos, cada uno con instrucción de texto e imagen opcional.
- Dado que dejo un campo obligatorio vacío, entonces el formulario me indica cuál falta antes de guardar.
- Toda guía nueva se crea en estado borrador y no es visible al público hasta publicarla (HU-15).
- Cada guía guarda quién la creó, quién la editó por última vez y cuándo.
Notas: en dominio, Guia contiene una lista ordenada de Paso. La regla «una guía publicada debe tener al menos un paso» vive en la entidad y se prueba con pruebas unitarias.
 
 
---
 
### HU-14 · Agregar imágenes a los pasos
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** personal del CLENA **quiero** subir una captura de pantalla a cada paso **para** que el usuario vea exactamente dónde hacer clic.
 
Prioridad: Should · Puntos: 5
 
Criterios de aceptación:
 
- Dado que edito un paso, cuando subo una imagen PNG, JPG o WEBP de máximo 5 MB, entonces queda asociada al paso.
- Dado que subo un archivo de otro tipo o más pesado, entonces el sistema lo rechaza con un mensaje claro.
- Dado que subo una imagen, entonces debo escribir un texto alternativo para lectores de pantalla.
- El almacenamiento de archivos se implementa mediante un proveedor externo de almacén de objetos
---
 
### HU-15 · Publicar, ocultar y reordenar guías
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** personal del CLENA **quiero** publicar u ocultar guías y cambiar el orden de los pasos **para** controlar qué ve el público y corregir el contenido.
 
Prioridad: Must · Puntos: 3  · Sprint 2
 
Criterios de aceptación:
 
- Dado que una guía está en borrador y tiene al menos un paso, cuando la publico, entonces aparece en el catálogo público.
- Dado que oculto una guía publicada, entonces desaparece del catálogo, pero el progreso de los usuarios en ella se conserva.
- Dado que reordeno los pasos, entonces el nuevo orden se refleja inmediatamente en la vista pública.
---
 
### HU-16 · Gestionar categorías
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** administrador **quiero** editar el nombre, ícono y orden de las categorías **para** adaptarlas a las necesidades de la sala.
 
Prioridad: Should· Puntos: 2
 
Criterios de aceptación:
 
- Dado que soy administrador, entonces puedo crear, editar y reordenar categorías.
- Dado que una categoría tiene guías, cuando intento eliminarla, entonces el sistema lo impide y me pide moverlas primero.
- La categoría inicial «Phishing» (id: 1, slug: phishing, nombre: Phishing, icono: shield-alert, orden: 1) viene creada en las semillas.
---
 
### HU-17 · Contenido: Smishing (Phishing por SMS)
 
**Autor:** Sair Javid Cervantes Rey
 
**Como** usuario de la plataforma **quiero** aprender a identificar mensajes de texto engañosos (smishing) con enlaces falsos **para** evitar robos de datos e infecciones en mi dispositivo.
 
Prioridad: Must · Puntos: 3  · Sprint 2
 
Criterios de aceptación:
 
- Las semillas incluyen la guía de Smishing en la categoría Phishing, explicando señales como urgencia, enlaces acortados o sospechosos y remitentes no verificados.
- Algunas guías tienen al menos una pregunta de práctica asociada (E3).
---
 
### HU-18 · Contenido: Vishing (Phishing por llamadas de voz)
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario de la plataforma **quiero** conocer las tácticas empleadas en engaños telefónicos (vishing) y suplantación de identidad **para** no entregar información confidencial durante llamadas entrantes.
 
Prioridad: Must · Puntos: 3 · Sprint 2
 
Criterios de aceptación:
 
- Las semillas incluyen la guía de Vishing en la categoría Phishing, con pautas para verificar la identidad del llamante y protocolos de respuesta ante solicitudes sospechosas.
- Cada guía tiene al menos una pregunta de práctica asociada.
---
 
### HU-19 · Contenido: Quishing (Phishing mediante códigos QR)
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario de la plataforma **quiero** comprender los riesgos asociados a la lectura de códigos QR maliciosos (quishing) **para** escanearlos de manera segura en espacios públicos y digitales.
 
Prioridad: Must · Puntos: 3  · Sprint 2
 
Criterios de aceptación:
 
- Las semillas incluyen la guía de Quishing en la categoría Phishing, enseñando a comprobar el dominio de destino antes de abrir el enlace del QR.
- La guía incluye ejemplos de etiquetas QR superpuestas y enlaces acortados fraudulentos.
---
 
### HU-20 · Contenido: Falso soporte técnico
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario de la plataforma **quiero** aprender a reconocer alertas engañosas de virus y solicitudes de acceso remoto no autorizadas **para** proteger mi equipo de fraudes de falso soporte.
 
Prioridad: Must · Puntos: 3 · Sprint 2
 
Criterios de aceptación:
 
- Las semillas incluyen la guía de Falso soporte técnico en la categoría Phishing, cubriendo emergentes sospechosos de navegador y llamadas no solicitadas de soporte.
- Las guías no usan marcas ni capturas que identifiquen a personas reales.
---
 
### HU-21 · Resolver una pregunta con retroalimentación inmediata
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** adulto mayor que terminó una guía **quiero** responder preguntas cortas y saber de inmediato si acerté y por qué **para** confirmar que entendí.
 
Prioridad: Must · Puntos: 3 · Sprint 2
 
Criterios de aceptación:
 
- Dado que abro una actividad, entonces veo una pregunta a la vez, con opciones grandes y el progreso de la actividad («Pregunta 2 de 4»).
- Dado que elijo una respuesta correcta, entonces veo una confirmación en verde con ícono y texto, y una explicación corta.
- Dado que elijo una respuesta incorrecta, entonces veo un mensaje amable («Casi. La respuesta correcta es...») con la explicación, sin sonidos ni colores que alarmen.
- Dado que termino la actividad, entonces veo cuántas respuestas acerté y si la aprobé (70 % o más, configurable).
- Dado que no aprobé, entonces puedo repetir la actividad o volver a la guía.
- El color nunca es la única señal de acierto o error: siempre hay texto e ícono.
Notas: la calificación y la regla de aprobación viven en el dominio (Intento.calificar()), sin dependencias de NestJS. El frontend nunca recibe cuál es la opción correcta antes de que el usuario responda.
 
 
---
 
### HU-22 · Crear actividades de práctica
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** personal del CLENA **quiero** tener la posibilidad de crear actividades con preguntas de selección múltiple asociadas a una guía **para** que los usuarios practiquen lo que leyeron.
 
Prioridad: Should · Puntos: 5 
 
Criterios de aceptación:
 
- Dado que edito una guía, cuando creo una actividad, entonces puedo agregar entre 1  y 10 preguntas.
- Dado que creo una pregunta, entonces escribo el enunciado, entre 2 y 4 opciones, marco exactamente una correcta y escribo una explicación.
- Dado que no marco ninguna opción correcta o marco más de una, entonces el sistema no guarda la pregunta y me dice por qué.
- Una pregunta puede incluir una imagen opcional (por ejemplo, una captura de una bandeja de entrada).
---
 
### HU-23 · Ver mi progreso
 
**Autor:** Yussef Kassem Issa
 
*Historia propia de Yussef: barra de progreso con los módulos completados.*
 
**Como** usuario que sigue varias guías **quiero** ver una barra de progreso por guía y la lista de lo que he completado **para** saber cuánto he avanzado y qué me falta.
 
Prioridad: Must · Puntos: 5 · Sprint 2
 
Criterios de aceptación:
 
- Dado que inicié sesión, entonces en «Mi progreso» veo por cada guía una barra con el porcentaje de guías completadas, acompañada del número.
- Una guía cuenta como completada cuando la leí hasta el último paso y, si tiene actividad, la aprobé.
- Dado que veo mi progreso, entonces las guías completadas tienen una marca visible y las pendientes un botón «Empezar».
- Dado que no he iniciado sesión, entonces esta sección me invita a crear una cuenta.
---
 
### HU-24 · Retomar donde quedé
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** usuario que no terminó una guía en su última visita **quiero** que la plataforma me ofrezca continuar en el paso donde quedé **para** no empezar de cero.
 
Prioridad: Should · Puntos: 3 
 
Criterios de aceptación:
 
- Dado que dejé una guía en el paso 4, cuando vuelvo a iniciar sesión, entonces mi página de inicio muestra «Continúa donde quedaste» con esa guía.
- Dado que elijo continuar, entonces la guía se abre en el paso 4.
---
 
### HU-25 · Reconocer mensajes fraudulentos (phishing)
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** adulto mayor que recibe correos y mensajes de supuestos bancos o entidades **quiero** practicar con ejemplos para distinguir un mensaje falso de uno real **para** no entregar mis datos ni mi dinero.
 
Prioridad: Must · Puntos: 5 · Origen: Alcance mínimo · Sprint 2
 
Criterios de aceptación:
 
- Las semillas incluyen una guía con las señales de alerta: urgencia, petición de claves o códigos, remitente extraño, enlaces que no coinciden y premios inesperados.
- Dado que hago la actividad de phishing, entonces veo al menos 5 mensajes simulados y respondo para cada uno «¿Es confiable o es un fraude?».
- Dado que respondo, entonces la retroalimentación señala sobre el mensaje dónde estaba la pista.
- Los mensajes simulados usan entidades ficticias (por ejemplo, «Banco Ejemplo») y enlaces que no llevan a ningún sitio real. Los textos alternativos de las imágenes también dicen que son simulados (por ejemplo, «Correo simulado de Banco Ejemplo, entidad ficticia»).
---
 
### HU-26 · Crear y cuidar contraseñas
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** visitante **quiero** aprender a crear una contraseña segura y fácil de recordar **para** proteger mis cuentas.
 
Prioridad: Must · Puntos: 3 · Sprint 3
 
Criterios de aceptación:
 
- Las semillas incluyen una guía sobre cómo armar una contraseña con una frase, por qué no repetirla y por qué no compartirla con nadie, ni siquiera con el personal.
- La guía incluye recomendaciones para computadores compartidos: no guardar contraseñas en el navegador y cerrar sesión al terminar.
- La actividad presenta contraseñas de ejemplo y pide clasificarlas como débiles o seguras.
---
 
### HU-27 · Identificar información confiable
 
**Autor:** Sair Javid Cervantes Rey
 
*Historia propia de Sair: aprender a buscar información en internet de forma segura.*
 
**Como** visitante que busca información de salud, trámites y noticias **quiero** aprender a revisar si una página es confiable **para** no tomar decisiones con información falsa.
 
Prioridad: Must · Puntos: 3  · Sprint 3
 
Criterios de aceptación:
 
- Las semillas incluyen una guía con una lista corta de verificación: quién publica, dirección del sitio (por ejemplo, terminaciones .gov.co), fecha y si otras fuentes dicen lo mismo.
- La actividad muestra titulares o páginas simuladas y pide decidir si son confiables.
---
 
### HU-28 · Botón de ayuda siempre visible
 
**Autor:** Sair Javid Cervantes Rey
 
*Historia propia de Sair: botón de ayuda siempre visible.*
 
**Como** adulto mayor **quiero** un botón de ayuda visible en todas las pantallas **para** resolver mis dudas sin depender de otra persona.
 
Prioridad: Must · Puntos: 3 · Sprint 3
 
Criterios de aceptación:
 
- Dado que estoy en cualquier pantalla, entonces veo un botón «Ayuda» grande, con texto, en la misma posición siempre.
- Dado que lo presiono, entonces veo tres opciones: «Preguntas frecuentes», «¿Qué significa esta palabra?» (glosario) y «Llamar a un monitor».
- Dado que las preguntas frecuentes o el glosario aún no están disponibles, entonces solo aparece la opción de llamar a un monitor.
---
 
### HU-29 · Solicitar ayuda presencial
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** visitante que no pudo resolver su duda **quiero** pedir ayuda indicando mi equipo y el tema **para** que un monitor venga a mi puesto sin que yo tenga que levantarme a buscarlo.
 
Prioridad: Must · Puntos: 5  · Sprint 3
 
Criterios de aceptación:
 
- Dado que elijo «Llamar a un monitor», entonces indico el número de equipo y elijo un tema de una lista corta.
- Dado que estaba en una guía, entonces la solicitud incluye automáticamente la guía y el paso donde estaba.
- Dado que envío la solicitud, entonces veo «Un monitor vendrá pronto» y mi posición en la cola.
- Dado que ya tengo una solicitud pendiente desde el mismo equipo, entonces el sistema no crea una duplicada y me muestra la existente.
- Puedo cancelar mi solicitud si resolví la duda por mi cuenta. La solicitud no exige haber iniciado sesión: basta con el número de equipo.
---
 
### HU-30 · Atender la cola de solicitudes
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** monitor de la sala **quiero** ver las solicitudes de ayuda en orden de llegada y marcar su estado **para** atender a quien lo necesita sin interrupciones desordenadas.
 
Prioridad: Must · Puntos: 5 · Origen: Alcance mínimo · Sprint 3
 
Criterios de aceptación:
 
- Dado que soy personal, entonces veo las solicitudes pendientes con equipo, tema, guía y paso, y tiempo de espera, ordenadas de la más antigua a la más reciente.
- Dado que tomo una solicitud, entonces pasa a «En atención» con mi nombre, para que otro monitor no la tome.
- Dado que la resuelvo, entonces la marco como «Resuelta» y puedo anotar un comentario breve opcional.
- La lista se actualiza sola al menos cada 15 segundos, sin recargar la página, mediante consultas periódicas desde el frontend (polling). No se usan WebSockets.
- Las transiciones de estado válidas: pendiente → en atención → resuelta → cancelada
---
 
### HU-31 · Ver los temas más consultados
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** coordinadora de la sala **quiero** ver qué guías y categorías se consultan más en un periodo **para** decidir qué contenido reforzar y dónde se concentran las dudas.
 
Prioridad: Must · Puntos: 5 · Sprint 3
 
Criterios de aceptación:
 
- Dado que abro el panel, entonces veo el top 10 de guías más abiertas y las consultas por categoría en un gráfico, con filtro por rango de fechas (últimos 7 días por defecto).
- Dado que veo el panel, entonces también veo cuántas solicitudes de ayuda hubo y los temas más pedidos.
- Dado que no hay datos en el rango, entonces el panel lo indica en lugar de mostrar gráficos vacíos.
- Las consultas del panel usan agregaciones en la base de datos, no cálculos en memoria sobre todos los registros. Con Prisma se usa groupBy o $queryRaw, y la tabla de consultas tiene un índice por guía y fecha.
---
 
### HU-32 · Ver el desempeño en las actividades
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** personal del CLENA **quiero** ver qué actividades y preguntas tienen más respuestas incorrectas **para** mejorar las guías que no se están entendiendo.
 
Prioridad: Should · Puntos: 3 
 
Criterios de aceptación:
 
- Dado que abro esta sección del panel, entonces veo por actividad el número de intentos y el porcentaje de aprobación.
- Dado que elijo una actividad, entonces veo el porcentaje de acierto de cada pregunta, de menor a mayor.
---
 
### HU-33 · Preguntas frecuentes
 
**Autor:** Diego Guerrero Canoles
 
*Historia propia de Diego: sección de preguntas frecuentes.*
 
**Como** usuario con dudas operativas **quiero** revisar una sección de preguntas frecuentes **para** resolver inquietudes rápidas sobre cómo usar la plataforma y la sala.
 
Prioridad: Should · Puntos: 3
 
Criterios de aceptación:
 
- Dado que abro las preguntas frecuentes, entonces las veo agrupadas por tema y puedo desplegar cada respuesta.
- Dado que soy personal, entonces puedo crear, editar, ordenar y ocultar preguntas.
- Las semillas incluyen al menos 8 preguntas reales, recogidas con el equipo G5 y el personal (por ejemplo, «¿Cómo imprimo?», «¿Cuánto tiempo puedo usar el equipo?»).
---
 
### HU-34 · Glosario de términos
 
**Autor:** Yussef Kassem Issa
 
*Historia propia de Yussef: glosario de términos.*
 
**Como** visitante con poca experiencia digital **quiero** consultar el significado de palabras como «descargar», «cuenta» o «pestaña» **para** entender las guías.
 
Prioridad: Should · Puntos: 3
 
Criterios de aceptación:
 
- Dado que abro el glosario, entonces veo los términos en orden alfabético con buscador, cada uno con una definición sencilla y, opcionalmente, una imagen.
- Dado que un término del glosario aparece en un paso de una guía, entonces se muestra resaltado y al tocarlo veo su definición sin salir de la guía.
- Dado que soy personal, entonces puedo administrar los términos.
- Las semillas incluyen al menos 20 términos.
---
 
### HU-35 · Calificar mi experiencia
 
**Autor:** Diego Guerrero Canoles
 
*Historia propia de Diego: calificar la experiencia con íconos rápidos.*
 
**Como** usuario que termina su sesión **quiero** calificar mi experiencia con caritas **para** ayudar a mejorar las herramientas de la institución.
 
Prioridad: Should · Puntos: 3 · Origen: I4-6
 
Criterios de aceptación:
 
- Dado que cierro sesión o termino una guía, entonces se me ofrece una calificación opcional con tres caritas grandes con texto («Me ayudó», «Más o menos», «No me ayudó»).
- Dado que califico, entonces puedo dejar un comentario opcional de máximo 300 caracteres.
- Dado que soy personal, entonces veo en el panel el resumen de calificaciones por periodo y por guía.
- La calificación es anónima si el usuario no inició sesión.
---
 
### HU-36 · Ajustar el tamaño de la letra
 
**Autor:** Diego Guerrero Canoles
 
*Historia propia de Diego: cambiar el tamaño del texto en la aplicación.*
 
**Como** adulto mayor con dificultades de visión **quiero** agrandar el texto de la aplicación con un botón **para** leer las guías con comodidad.
 
Prioridad: Must · Puntos: 3 · Origen: I3-1, I4-4 · Sprint 3
 
Criterios de aceptación:
 
- El tamaño base del texto es de al menos 18 px.
- Dado que estoy en cualquier pantalla, entonces tengo controles visibles «A-» y «A+» con al menos tres tamaños (normal, grande, muy grande).
- Dado que agrando el texto, entonces el diseño se reacomoda sin cortar texto ni generar desplazamiento horizontal.
- Dado que no inicié sesión, entonces la preferencia se recuerda en ese navegador; si inicié sesión, se guarda en mi perfil.
- El zoom del navegador hasta 200 % también funciona sin romper el diseño.
---
 
### HU-37 · Modo de alto contraste
 
**Autor:** Sair Javid Cervantes Rey
 
*Historia propia de Sair: ajustar tamaño de letra y contraste (el tamaño de letra se registra además en HU-36).*
 
**Como** adulto mayor con baja visión **quiero** activar un modo de alto contraste **para** distinguir mejor el texto y los botones.
 
Prioridad: Must · Puntos: 3  · Sprint 3
 
Criterios de aceptación:
 
- El modo normal cumple contraste mínimo 4,5:1 para texto (WCAG 2.1 AA).
- Dado que activo el alto contraste, entonces los colores cambian a una paleta de contraste de al menos 7:1 (WCAG AAA).
- Los botones y enlaces se distinguen por forma o subrayado, no solo por color.
- La preferencia se guarda igual que la del tamaño de letra.
---
 
### HU-38 · Navegación con teclado y lectores de pantalla
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** persona con dificultades motrices o visuales **quiero** usar toda la plataforma con el teclado y con un lector de pantalla **para** no depender del ratón ni de leer la pantalla.
 
Prioridad: Must · Puntos: 5  · Sprint 3
 
Criterios de aceptación:
 
- Todas las acciones se pueden hacer con Tab, Shift+Tab, Enter y Espacio, en un orden lógico.
- El elemento enfocado tiene un indicador visible y grueso.
- Todos los campos de formulario tienen etiqueta, y los errores se anuncian a los lectores de pantalla.
- Todas las imágenes tienen texto alternativo, y los íconos decorativos están ocultos para lectores de pantalla.
- Cada pantalla pasa dos verificaciones automáticas en CI: Lighthouse CI con puntaje de accesibilidad de al menos 90 y axe (por ejemplo, @axe-core/playwright) sin violaciones graves o críticas. El job falla si alguna no se cumple.
---
 
### HU-39 · Uso desde el celular
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** visitante con su celular **quiero** que la plataforma se vea bien en pantallas pequeñas **para** seguir las guías desde mi teléfono mientras uso el computador.
 
Prioridad: Must · Puntos: 3 · Sprint 3
 
Criterios de aceptación:
 
- Todas las pantallas funcionan desde 360 px de ancho sin desplazamiento horizontal.
- Los botones y zonas táctiles miden al menos 44 × 44 px.
- En celular, una guía se puede seguir en una pestaña mientras el usuario practica en el computador.
---
 
### HU-40 · Tutorial de primera visita
 
**Autor:** Diego Guerrero Canoles
 
*Historia propia de Diego: tutorial interactivo para quien usa los equipos por primera vez.*
 
**Como** persona que usa la plataforma por primera vez **quiero** un recorrido corto que me muestre dónde está cada cosa **para** aprender a usarla por mi cuenta.
 
Prioridad: Should · Puntos: 3 · Origen: I4-1
 
Criterios de aceptación:
 
- Dado que entro por primera vez en ese navegador o con mi cuenta, entonces se me ofrece un recorrido de máximo 5 pasos: categorías, buscador, tamaño de letra, botón de ayuda y mi progreso.
- Dado que estoy en el recorrido, entonces puedo avanzar, retroceder u omitirlo en cualquier momento.
- Dado que lo omití, entonces puedo volver a verlo desde el botón de ayuda.
---
 
### HU-41 · Lectura en voz alta de las guías
 
**Autor:** Yussef Kassem Issa
 
*Historia propia de Yussef: lectura en voz alta del contenido de las guías.*
 
**Como** persona con dificultades visuales **quiero** que la aplicación lea en voz alta cada paso de la guía **para** aprender sin depender de leer la pantalla.
 
Prioridad: Could · Puntos: 5
 
Criterios de aceptación:
 
- Dado que estoy en un paso, cuando presiono «Escuchar», entonces se lee el texto del paso en español.
- Dado que está leyendo, entonces puedo pausar, repetir y ajustar la velocidad (normal o lenta).
- Dado que avanzo de paso, entonces la lectura anterior se detiene.
Notas: se puede implementar solo en el frontend con la Web Speech API del navegador, sin costo de backend. Verificar que los computadores de la sala tengan parlantes o audífonos.
 
 
---
 
### HU-42 · Incentivo de cumplimiento
 
**Autor:** Sair Javid Cervantes Rey
 
*Historia propia de Sair: ver el avance y recibir un certificado de cumplimiento.*
 
**Como** adulto mayor que completó una categoría **quiero** recibir un incentivo por puntos **para** sentirme motivado y demostrar lo que aprendí.
 
Prioridad: Could · Puntos: 5 
 
Criterios de aceptación:
 
- Dado que completé todas las guías obligatorias de una categoría, entonces obtendré una serie de puntos asociadas a mi perfil donde se podrá ver qué tanto he desarrollado en la plataforma
- Todas las guías tendrán asociadas una serie de puntos por ser completados en su totalidad, y como usuario podré ver de dónde vienen mis puntos.
---
 
### HU-43 · Búsqueda por voz
 
**Autor:** Andrés Camilo Badillo Cervera
 
*Historia propia de Andrés: búsqueda por voz.*
 
**Como** visitante con dificultades de movimiento en las manos **quiero** buscar guías hablando **para** no tener que escribir.
 
Prioridad: Could · Puntos: 5 
 
Criterios de aceptación:
 
- Dado que el navegador lo permite, entonces junto al buscador aparece un botón de micrófono con texto.
- Dado que hablo, entonces mi frase aparece escrita en el buscador y se ejecuta la búsqueda de HU-11.
- Dado que el navegador no lo permite o no hay micrófono, entonces el botón no aparece.
Notas: Web Speech API; el soporte varía según el navegador y requiere conexión. Confirmar qué navegador y si hay micrófonos en la sala.
 
 
---
 
### HU-44 · Interfaz en inglés
 
**Autor:** Yussef Kassem Issa
 
*Historia propia de Yussef: cambiar el idioma entre español e inglés.*
 
**Como** visitante extranjero **quiero** cambiar el idioma de la interfaz entre español e inglés **para** entender los menús.
 
Prioridad: Won’t· Puntos: 3
 
Criterios de aceptación:
 
- Dado que elijo «English», entonces todos los textos fijos de la interfaz (menús, botones, mensajes) se muestran en inglés.
- El contenido de las guías se mantiene en español, con un aviso en inglés que lo indica.
---
 
### HU-45 · Acceso rápido por código QR
 
**Autor:** Equipo de Introducción en conjunto con el equipo de Backend (8.º semestre)
 
**Como** visitante en la sala **quiero** escanear un código QR en el puesto **para** abrir directamente la plataforma o una guía en mi celular, sin escribir la dirección.
 
Prioridad: Must · Puntos: 2 · Origen: Alcance mínimo · Sprint 3
 
Criterios de aceptación:
 
- Dado que escaneo el código QR impreso en el puesto, entonces la aplicación se abre en la guía o categoría correspondiente.
- No se requiere inicio de sesión para acceder mediante el código QR.
- Dado que soy personal del CLENA, entonces puedo descargar e imprimir el QR de la plataforma, de cada categoría y de cada guía.
---
 
Dado que escaneo el código QR impreso en el puesto, entonces la aplicación se abre en la guía o categoría correspondiente.
No se requiere inicio de sesión para acceder mediante el código QR.
Dado que soy personal del CLENA, entonces puedo descargar e imprimir el QR de la plataforma, de cada categoría y de cada guía.
