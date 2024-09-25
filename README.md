# API-Mule
API proyect hecho con MuleSoft
<h3>Requsitos</h3>
<ul>
  <li>Anypoint Studio 7</li>
  <li>Mule 4</li>
  <li>JDK 8 u 11</li>
  <li>Cliente REST de tu elección (Postman)</li>
  <li>Acceso a línea de comando con permisos de administrador</li>
</ul>
<h2>Tabla de contenidos</h2>
<ul>
  <li><a href="descripcion">Descripción</a></li>
  <ul>
    <li><a href="uso">Uso</a></li>
  </ul>
  <li><a href="paso">Paso a Paso</a></li>
  
  <ul>
    <li><a href="cuenta">Creación de cuenta en Anypoint Platfrom</a></li>
    <li><a href="descarga">Descarga de Anypoint Studio</a></li>
    <li><a href="proyecto">Creación del proyecto</a></li>
    <li><a href="listener">Añadiendo y configurando HTTP Listener Connector</a></li>
    <li><a href="global">Generando propiedades Globales</a></li>
    <li><a href="bd">Añadiendo la base de datos</a></li>
    <li><a href="json">Transformando la respuesta en formato JSON</a></li>
    <li><a href="encriptado">Encriptando la información con Secure Tool jar</a></li>
    <li><a href="cloudhub">Despliegue en CloudHub</a></li>
    <li><a href="auto">Configurando API AutoDiscovery</a></li>
    <li><a href="politica">Política ClientID para Mule</a></li>    
  </ul>
  <li><a href="agradecimientos">Agradecimientos</a></li>
</ul>

<h2 href="descripcion">Descipción del Proyecto</h2>
API Mule PSP es un proyecto básico utilizando buenas prácticas de programación para la petición de solicitudes HTTP a una base de datos de prueba de Mule. El proyecto esta completamente realizado en Anypoint Studio 7 utilizando Mule 4, es necesario tener ambas versiones para poder generar el proyecto actual, de lo contrario puedes encontrarte con varios problemas a la hora de intentar implementar las soluciones sugeridas en el proyecto.
El proyecto cuenta con Autorizaciones básica utilizando ClientID Enforcement, permitiendo la protección de los datos a terceros. Se encuentra alojada en CloudHub utilizando Anyponit Platform para su gestión. También encripta la información sensible de la aplicación antes del despliegue de la misma utilizando el algoritmo Blowfish y la herramienta propia de encriptación de Mule. 
Se hace uso de propiedades de seguirdad y propiedades de entorno, protegidas utilizando un entorno global para el acceso a ellas.
La aplicación se encuentra alojada en CloudHub y usa AutoDiscovery para la instancia y gestión del API. 
La API hace una única petición a la base de datos de solicitud de toda la información contenida en la tabla customers.
<h3 href="uso">Uso</h3>
Para poder utilizar la API es necesario utilizar un Cliente REST o por medio del navegar, utilizando la siguiente liga: https://muleapisps-svx0mf.5sc6y6-1.usa-e2.cloudhub.io/api/v1/sps/customers/
Para poder acceder a la información se solicitará Basic Auth, por tanto te sugiero que generes la API por ti mismo.
<h3>instalación</h3>
Para instalar este repositorio solo necesitas dar clic en code / download zip y extraer el zip en una carpeta de tu elección.
<h2 href="paso">Paso a paso</h2>
<h3 href="cuenta">Creación de cuenta en Anypoint Platfrom</h3>
<p></p>Antes de empezar, para poder desplegar tu aplicación Mulesoft es necesario utilizar Anypoint Platform para alojar tu aplicación en CloudHub. Puedes registrar una cuenta gratis en el siguiente enlace: https://anypoint.mulesoft.com/login/signup?apintent=generic.</p>
<h3 href="descarga">Descarga de Anypoint Studio</h3>
<p>Una vez realizada registrada la cuenta, es necesario descargar el IDE de Mulesoft, Anypoint Studio. Puedes descargarlo directamente en su sitio web https://www.mulesoft.com/, en el apartado de productos, integración, Studio; o en el siguiente enlace: https://www.mulesoft.com/platform/studio.</p>
<p>Antes de descargarlo, si no has creado una cuenta en Mulesoft, se te solicitará crear una cuenta de Mulesoft.</p>
<p>Para descargar Anypoint Studio, es necesario: </p>
<ul>
  <li>Java JDK 8</li>
  <li>Tener instalado Git</li>
  <li>Asegurarse de tener una cuenta Anypoint Platform</li>
</ul>
<p>Una vez realizada la cuenta en Mulesoft, vamos a acceder a ella e iremeos al apartado de Anypoint Studio y seleccionaremos <strong>Download</strong>. Realizado esto, nos redirigira a la página para descargar, a lo cual seleccionaremos Anypoint Studio 7 y Mule4, llenamos los datos solicitados y daremos en descargar. Al descargarlo nos enviarán un correo con el enlace de descarga. Es importante descargar las vesion más actual ya que de lo contrario no se podrán utilizar ciertos elementos vistos en este repositorio.</p>
<p>Una vez instalado Anypoint Studio, nos requerirá conceder permisos para el firewall, los cuales debemos aceptar ya que de lo contrario no podrá hacer uso del IDE.</p>
<p>Ya instalado Anypoint Studio, accederemos a la carperta de Anypoint Studio e iniciaremos el programa. Al iniciarlo, nos aparecerá una venta solicitandonos una ruta en la cual guardaremos nuestros proyectos. Despúes nos aparecerá un mensaje de bienvenida indicarndo todas las actualizaciones de la versión.</p>
<h3 href="proyecto">Creación del proyecto</h3>
<p>Para poder generar un nuevo proyecto en Anypoint Studio, accederemos al menu de <strong>File / New Mule Project</strong>. Nos aparecerá una ventana en la cual podremos configurar y detallar nuestro proyecto. En el campo de nombre le colocaremos el nombre del proyecto y generaremos el proyecto con <strong>Finish</strong>.</p>
<h3 href="listener">Añadiendo y configurando HTTP Listener Connector</h3>
<p>Primero añadiremos un HTTP Listener, para esto iremos a la parte derecha de la pantalla, en la ventana <strong>Mule Palette</strong>, econtraremos el conector HTTP Listener el cual arrastrarremos hasta el lienzo. *Un HTTP Listener es un punto final HTTP que escucha peticiones HTTP para una URL que definimos.</p>
<p>Ahora seleccionaremos el HTTP Listener Connector, y en el editor de propiedades que se encuentra en la parte inferior, seleccionaremos el símbolo de adicón verde. Esto nos permitirá especificar la configuración del conector. Por el momento dejaremos todo como se encuentra y daremos generar</p>
<h3 href="global">Generando propiedades Globales</h3>
<p>Promoviendo las buenas prácticas, procederemos a generar propiedades globales con las cuales protegeremos la información sensible de nuestra aplicación. Ya que queremos tener varios perfiles con los cuales trabajar (uno local y otro de producción) generaremos propiedades para cada uno. Para esto, procederemos a generar dos archivos en la carpeta: src/main/resources. Daremos clic derecho a la carpeta/ New / File. Los archivos tendran el nombre de:</p>
<ul>
  <li>local.properties</li>
  <li>prod.properties</li>
</ul>
<p>En cada uno de los archivos procederemos a definir las propiedades necesarias para poder solicitar y obtener la respuesta de la petición. Las propiedades en ambos casos serán:</p>
<ul>
  <li>http.listener.host=0.0.0.0</li>
  <li>http.listener.port=8081</li>
  <li>database.host=mudb.learn.mulesoft.com</li>
  <li>database.port=3306</li>
  <li>database.user=mule</li>
  <li>database.password=mule</li>
  <li>database.name=training</li>
</ul>

<p>Una vez generados los archivos con las propiedades, en la carpeta: src/main/mule; generaremos un <strong>Mule Configuration File</strong>. Para esto daremos clic derecho a la carpeta / New / Mule Configuration File. A éste archivo lo llamaremos <strong>global.xml</strong>. Una vez generado, procederemos a regresar a el archivo principal de nuestra aplicación e iremos a la vista <strong>Configuration XML</strong>. Podremos revisar que en esta vista podemos ver el código XML de nuestra aplicaión. Dentro del código podremos observar que es un lenguaje por etiquetas, buscaremos la etiqueta <strong>http:listener-confi</strong>, la seleccionaremos hasta su final y la cortaremos en el archivo <Strong>Global.xml</Strong>, dentro de la etiqueta <strong>Mule</strong>. Es importante cortar la etiqueta ya que no se pueden repetir los nombre de los elementos en Anypoint Studio. Realizado esto regresaremos a nuestro <strong>Http Listener</strong> dentro de nuestro archivo principal. En las propiedades de nuestro Http Listener retornaremos a nuestro Connector Configuration, le daremos clic a la ventana con un lápiz que se encuentra a lado del símbolo de adición verde. Esto nos permitirá editar la configuración.</p>
<p>Ahora configuraremos las propiedades de nuestro listener, las propiedades quedarian de la siguiente forma:</p>
<ul>
  <li>Host: ${http.listener.host}</li>
  <li>Port: ${http.listener.port}</li>
</ul>
<p>Como estamos utilizando las propiedades globales, utilizamos "${}" para poder invocarlas y como queremos invocarlas debemos generar nuestra configuración global.</p>
<p>Para generar la configuración global, iremos a nuestro archivo <strong>Global.xml</strong>, en la vista <strong>Global Elements</strong>, podremos encontrar la opción create, con la cúal nso abrira una ventana que nos permitira añadir la configuración de propiedades. En el buscador podemos buscar <strong>Configuration Properties</strong> o en el menú Global Configuration la podremos encontrar. Le daremos el nombre <strong>${env}.properties</strong></p>, lo que nos permitirá elegir el archivo de propiedades segun el ambiente. Para que Anypoint Studio pueda reconocer la variable "env" en el mismo archivo Global.xml, en la vista Global Elements, daremos nuevamente a la opción Create y buscaremos por <strong>Global Property</strong>, a la cual le daremos el nombre <strong>env</strong> y el valor <strong>local</strong>. Esto únicamente será para trabajar en un entorno local y poder generar las pruebas necesarias.
<h3 href="bd">Añadiendo la base de datos</h3>
<p>Generadas las propiedades globales y las propiedades de ambiente, procederemos a generar la conexión con la base de datos. Para esto, en el archivo principal, en la vista <strong>Message Flow</strong>, en el Mule Palette buscaremos <strong>Database Select</strong>, arrastraremos el elemento dentro del flujo y daremos clic para abrir las propiedades. Dentro de <strong>Basic Settings</strong> / Connector Configuration, le daremos clic al símbolo de adición verde. Dentro de la ventana, en el apartado de General, buscaremos la opción Connection a la cual seleccionaremos <strong>MySQL Connection</strong>, esto debido a que es el sistema de gestión utilizado por la base de datos que estaremos utilizando. En el apartado de <strong>Required Libraries</strong> le daremos a Modify y seleccionaremos las recomendadas por el sistema.</p>
<p>Dentro del apartado Connection que se despleaga tras seleccionar el sistema de gestión, pondremos las siguientes propiedades:</p>
<ul>
  <li>host: ${database.host}</li>
  <li>port: ${database.port}</li>
  <li>user: ${database.user}</li>
  <li>password: ${database.password}</li>
  <li>Database: ${database.name}</li>
</ul>
<p>Le daremos Ok. En las propiedades del <strong>Database Select</strong>, en el apartado de Query pondremos las siguiente query: <strong>SELECT * FROM customers;</strong>; esta query nos permite revisar toda la información de la tabla customers.</p>
<h3 href="json">Transformando la respuesta en formato JSON</h3>
<p>Cuando generamos una solicitud a una base de datos, Anypoint Studio transformará la información recibida y la transformará en un objeto propio del IDE, por esto mismo es necesario transformar nuestra respuesta. Para esto procederemos a ir a nuestro archivo principal, en la vista Message Flow, en el Mule Palette buscaremos <strong>Transform message</strong>. Lo arrastraremos y lo pondremos dentro del flujo de la solicitud, le daremos clic para entrar a sus propiedades. Dentro de las propiedades nos aparecerá un recuadro llamado Output, el cual recibe informacion en formato YAML, en éste pondremos los siguiente:</p>
<ul>
  <li>output application/json</li>
  <li>---</li>
  <li>payload</li>
</ul>
<p>Con este formato estamos indicando que queremos transformar el contenido de la respuesta a un formato JSON. Le daremos guardar</p>
<h3 href="encriptado">Encriptando la información con Secure Tool jar</h3>
<p>Antes de poder deplegar nuestra aplicación a producción o cualquier otro ambien fuera de local, por motivos de seguridad de la API, procederemos a encriptar la información sensible para que solo nosotros o personas a las cuales les demos acceso puedan entrar a ella. Para empezar generaremos un archivo de propiedades de seguridad por ambiente generado. Estos archivos se alojarán dentro de src/main/resources; el nombre de los archivos será:</p>
<ul>
  <li>local.secure.properties</li>
  <li>prod.secure.properties</li>
</ul>
<p>En ambos archivos pondremos el siguiente par de claves:</p>
<ul>
  <li>example.username=</li>
  <li>example.password=</li>
</ul>
<p>Recomiendo que cambies cada uno dependiendo del ambiente.</p>
<p>Ahora necesitamos usar el apr de claves, para esto en el archivo principal, en la vista Message Flow, dentro de Mule Palette, buscaremos <strong>Logger</strong>, lo arrastramos dentro del flujo y seleccionamos para acceder a sus propiedades. Dentro de las propiedades, en Generic, Message,d aremos clic al boton de función para poder habilitar la vista gráfica, permitienedo generar código YAML con el cual daremos la instrucción de utilizar el par de claves generado, la instrucción es la siguiente:</p>
<ul>
  <li>output application/java</li>
  <li>---</li>
  <li>"Username: " ++ Mule::p("secure.example.username")</li>
  <li>++ " - " ++</li>
  <li>"Password: " ++ Mule::p("secure.example.password")</li>
</ul>
<p>Ahora procederemos a encriptar le par de claves. Para esto iremos al siguiente enlace: https://docs.mulesoft.com/mule-runtime/latest/secure-configuration-properties#secure_props_tool y decargaremos el archivo jar <strong>Secure Properties Tool</strong>. Realizado esto, abriremos una terminal y accederemos a la ruta donde se encuentra el archivo. Dentro de la carperta pondremos el siguiente comando: <strong>java -cp secure-properties-tool.jar com.mulesoft.tools.SecurePropertiesTool string encrypt Blowfish CBC PSP "valor de example.username"</strong>; esto lo haremos por cada par de claves en cada archivo de propiedades de seguridad. Al ejecutar el comando nos aparecerá el valor encriptado usando Blowfish, este valor lo sustituiremos por el valor de cada uno de nuestro par de claves utilizando <strong>![]</strong>,esto para que la aplicación reconozca que está cifrado.</p>
<p>Realizado lo anterior, procederemos air al archivo global.xml, en la vista Message Flow, en Mule palette, daremos clic en <strong>buscar en Exchange</strong> y buscaremos <strong>Mule Secure Configuration Property Extension</strong>; le daremos en Add y Finish. Iremos a la vista Global Elements y Create buscaremos <strong>Secure Properties Config</strong> y pondremos lo siguiente:</p>
<ul>
  <li>File: ${env}.secure.properties</li>
  <li>Key: ${secure.key}</li>
  <li>Algorithm: Blowfish</li>
</ul>
  <p>Terminando le daremos Ok.</p>
<p>Ahora, procederemos a dar clic derecho a nuestro proyecto y buscaremos la opcion Run As / Run configurations. Al darle clic nos aparecerá la venta de configuración. En General nos aparecerás las aplicaciones que tenemos y seleccionaremos la que estamos creando. En la pestaña Environment, añadiremos nuevas variables de entorno:</p>
  <ul>
    <li>Name: env / Value: local</li>
    <li>Name: secure.key / Value: PSP</li>
  </ul>
<p>Con esto le indicamos a nuestra aplicacón que al iniciar tendrá estás variables. El valor PSP fue asignado al encriptar el apr de claves.</p>
<p>Finalizado este punto, podremos hacer el despliegue de nuestra aplicación en Cloudhub</p>
<h3 href="cloudhub">Despliegue en CloudHub</h3>
<p>Para poder desplegar nuestra API en CloudHub debemos dar clic derecho a nuestra carpeta principal del proyecto "API-Mule", buscaremos la opción Anypoint Platform/deploy to CloudHub. Al hacer esto, nos perdirá que ingresemos nuestro usuario y contraseña de Anypoint Platform. Una vez ingresados nuestros datos, aparecerá la ventana de Anypoint Platform y opciones de entorno.</p>
<p>En este caso, utilizaremos <strong>SandBox</strong>. Procederemos abrindarle un nombre a nuestra aplicación, seleccionaremos el objetivo de despliegue (en nuestro caso US East), la versión de Run Time la cuál debe coincidir con la de nuestro proyecto, al igual que la version Java. Ahora, procederemos a generar las propiedades. Para esto iremos al apartado Properties e iremos añadiendo las propiedades globales usadas:</p>
<ul>
  <li>env:prod (esto indica que estaremos usando el perfil de produción)</li>
  <li>secure.key:PSP</li>
</ul>
<p>Hecho esto, le daremos a Deploy lo que generará nuestra aplicación dentro de Anypoint Platform</p>
<p>Finalizada la generación, nos indicará que ha sido generada la aplicación con éxito y podremos verla en el explorador o podremos utilizar nuestro programa de pruebas API. Podemos acceder a Anypoint Platform, en el menú superior izquierdo en el apartado de Runtime Manager; nos mostrara el catálogo de ambientes que tenemos en la cuenta y las aplicaciones generadas por ambiente. Puedes dar clic en la apliación que acabamos de generar y verificar la información que nos brinda la plataforma. En el apartado de <strong>Settings</strong> nos mostrará información del estado de nuestra aplicación y un End Point Público con el cual podras utilizar como URL para las peticiones.</p>
<h3 href="auto">Configurando API AutoDiscovery</h3>
<p>Para poder utilizar AutoDiscovery API, debemos entrar a AnypointPlatform con nuestras credenciales, en el menú principal, seleccionaremos APi Manager.</p>
<p>Para empezar seleccionaremos el ambiente a utilizar, en este caso SandBox, lo cual nos abrira el panel con todas las API generadas que tenemos en la plataforma. Seleccionaremos Add API / New API, lo cual nos permitirá generar nuestra API. El RunTime a elegir sera Mule Gateway y daremos en Next. Le daremos Create New API, le daremos un nombre de nuestra elección y elegiremos el Asset Type HTTP API y Next.</p>
<p>Una vez generada nuestra API aparecerá inactiva, esto debido a que no hemos implementado ninguna aplicación a la misma. Para direccionar nuestra aplicación a la instancia, en el apartado de Settings de la API, podremos observar que se encuetra un API Instance ID, lo copiaremos y dentro de nuestros archivos de propiedades de nuestra aplicación añadiremos una nueva propiedad llamada <strong>api.id</strong> con el valor que acabamos de copiar, así en cada archivo por ambiente.</p>
<p>Ahora, dentro de global.xml, en la vista Global Elements, Create, buscaremos AutoDiscovery en donde pondremos los siguiente valores:</p>
<ul>
  <li>API id: ${api.id}</li>
</ul>
<p>Y seleccionaremos el nombre de flujo que nos aparece y Ok.</p>
<p>Finalizado el último paso, procederemos a volver a Anypoint Platform, en API Manager podremos observar el boton Environment, dándole clic nos abrira una ventana con el ClientID y el Client secret; estos valores los pondremos dentro de nuestra aplicación. Para esto daremos clic a nuestra aplicacion e iremos al menú Window / Preferences / AnypointStudio / API Manager / Environment Credentials y colocaremos las credenciales correspondientes</p>
<p>Para proteger esta información a la hora de desplegar nuestra aplicación, podemos ir al archivo mule-artifact.json y añadir la propiedad "Security Properties" y con los valores a proteger ["secure.key", "anypoint.platform.client_id","anypoint.platform.client_secret"]. Guardamos todo y nuevamente realizamos el proceso de despliegue en CloudHub añadiendo las nuevas propiedades anypoint.platform.client_id y client_secret con sus credenciales correspondientes. Ahora podemos realizar pruebas en tu entorno preferido con nuestro endpoint publico añadiendo la ruta "/api/v1/sps/customers", lo cual activara nuestra API en API Manager</p>
<h3 href="politica">Política ClientID para Mule</h3>
<p>Podemos generar políticas para solicitar un par de claves y proteger quien puede tener acceso a nuestra API a pesar de tener el endpoint denegando el acceso. Para esto iremos a AnypointPlatform / API Manager, seleccionaremos nuestra API e iremos al apartado de Polices. Dentro de Polices / API-level Polices, añadiremos una nueva política y seleccionaremos Configure Client ID Enforcement policy y pondremos la opción HTTP Basic Authentication Header y generamos la política. Al intentar probar nuevamente nuestra API podemos verificar que ahora nos muestra el mensaje "Authentication denied.", para poder utilizar nuestra API ahora tendremos que poner las credenciales correspondientes en el apartado de Autenticación. Para obtener las credenciales, iremos a Anypoint Platform / Exchange; da clic en la API creada,e sto abrira una vista previa del API. Clic en Request Acces, selecciona la instancia del API y abre el Application Dropdown. Esto te permitirá crear una nueva liga de aplicación, da clic en ella y dale un nombre, crea la aplicación y da clic en Request Acces. Agrega las credenciales a tu cliente REST en el apartado de Autorización busca la opción Basic Auth y pega el par de claves proporcionadas. Ahora solo tú y con quien compartas éstas claves podrán ahcer uso de tu API.</p>

<h2 href="agradecimientos">Agradecimientos</h2>
Agradezco a PSP por mostrarme que existe Mule. Fue interesante su implementación y curva de aprendizaje. Aún falta mucho por aprender y si tienes dudas con respecto a Mule o Anypoint, te recomeindo acudir a sus Foros o la su documentación oficial.






