# API-Mule
API proyect made with Mulesoft

<h1>Paso a paso</h1>
<h2>Creación de cuenta en Anypoint Platfrom</h2>
<p></p>Antes de empezar, para poder desplegar tu aplicación Mulesoft es necesario utilizar Anypoint Platform para alojar tu aplicación en CloudHub. Puedes registrar una cuenta gratis en el siguiente enlace: https://anypoint.mulesoft.com/login/signup?apintent=generic.</p>
<h2>Descarga de Anypoint Studio</h2>
<p>Una vez realizada registrada la cuenta, es necesario descargar el IDE de Mulesoft, Anypoint Studio. Puedes descargarlo directamente en su sitio web https://www.mulesoft.com/, en el apartado de productos, integración, Studio; o en el siguiente enlace: https://www.mulesoft.com/platform/studio.</p>
<p>Antes de descargarlo, si no has creado una cuenta en Mulesoft, se te solicitará crear una cuenta de Mulesoft.</p>
<p>Para descargar Anypoint Studio, es necesario: </p>
<ul>
  <li>Java JDK 8</li>
  <li>Tener instalado Git</li>
  <li>Asegurarse de tener una cuenta Anypoint Platform</li>
</ul>
<p>Una vez realizada la cuenta en Mulesoft, vamos a acceder a ella e iremeos al apartado de Anypoint Studio y seleccionaremos <strong>Download</strong>. Realizado esto, nos redirigira a la página para descargar, a lo cual seleccionaremos Anypoint Studio y Mule4, llenamos los datos solicitados y daremos en descargar. Al descargarlo nos enviarán un correo con el enlace de descarga</p>
<p>Una vez instalado Anypoint Studio, nos requerirá conceder permisos para el firewall, los cuales debemos aceptar ya que de lo contrario no podrá hacer uso del IDE.</p>
<p>Ya instalado Anypoint Studio, accederemos a la carperta de Anypoint Studio e iniciaremos el programa. Al iniciarlo, nos aparecerá una venta solicitandonos una ruta en la cual guardaremos nuestros proyectos. Despúes nos aparecerá un mensaje de bienvenida indicarndo todas las actualizaciones de la versión.</p>
<h2>Creación del proyecto</h2>
<p>Para poder generar un nuevo proyecto en Anypoint Studio, accederemos al menu de <strong>File / New Mule Project</strong>. Nos aparecerá una ventana en la cual podremos configurar y detallar nuestro proyecto. En el campo de nombre le colocaremos el nombre del proyecto y generaremos el proyecto con <strong>Finish</strong>.</p>
<h3>Añadiendo y configurando HTTP Listener Connector</h3>
<p>Primero añadiremos el HTTP Listener, para esto iremos a la parte derecha de la pantalla, en la ventana <strong>Mule Palette</strong>, econtraremos el conector HTTP. Esté será seleccionado y arrastrado hasta el lienzo. *Un HTTP Listener es un punto final HTTP que escucha peticiones HTTP para una URL que definimos.</p>
<p>Ahora seleccionaremos el HTTP Listener Connector, y en el editor de propiedades abajo, seleccionaremos el símbolo de adicón verde. Esto creará un archivo de configuración bajo la configuración Global de elementos</p>


