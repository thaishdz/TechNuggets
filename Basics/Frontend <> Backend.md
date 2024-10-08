
# ¿Cómo se comunica el Frontend con el Backend?

El Front se comunica con el Back mediante __APIs__ usando el protocolo `HTTP` o `WebSockets`, dependiendo del tipo de interacción.


# Vale pero, cómo se hace?

Para que el frontend y el backend se conecten y se comuniquen, utilizan protocolos y métodos específicos que permiten enviar y recibir información. Vamos a ver los detalles de esa conexión:

1. Protocolo HTTP/HTTPS:

La conexión entre el frontend y el backend generalmente se realiza a través de HTTP o HTTPS (si es seguro). Es el mismo protocolo que usas para navegar en Internet, pero en este caso, es el canal de comunicación entre las dos partes:

	•	Frontend (navegador): hace solicitudes HTTP(S) al servidor del backend.
	•	Backend (servidor): recibe esas solicitudes, las procesa, y responde al frontend.

Tipos de solicitudes HTTP más comunes:

	•	GET: Para obtener datos del servidor. Ejemplo: Cuando cargas una página, el frontend hace un GET para obtener la información que necesita mostrar.
	•	POST: Para enviar datos al servidor. Ejemplo: Cuando envías un formulario de registro, el frontend usa POST para mandar esos datos al backend.
	•	PUT/PATCH: Para actualizar datos existentes en el servidor.
	•	DELETE: Para borrar datos en el servidor.

2. Conexión mediante APIs REST:

El frontend se conecta al backend a través de APIs REST, que son endpoints o rutas en el servidor donde el frontend puede hacer peticiones y recibir respuestas.

Ejemplo:

	•	El frontend hace un GET a https://api.misitio.com/users/123, y el backend responde con los datos del usuario 123 en formato JSON.
	•	Si quieres actualizar la información de ese usuario, el frontend haría un PUT o PATCH a esa misma ruta con los nuevos datos.

3. Fetch o Axios (Frontend):

Para hacer las solicitudes HTTP, el frontend usa herramientas como:

	•	Fetch API (nativa en JavaScript):

fetch('https://api.misitio.com/users', {
    method: 'GET'
})
.then(response => response.json())
.then(data => console.log(data));


	•	Axios (una librería popular para realizar solicitudes):

axios.get('https://api.misitio.com/users')
  .then(response => console.log(response.data));



Estas herramientas permiten que el frontend haga peticiones a las rutas del backend y reciba respuestas.

4. Backend (Servidor API):

El backend escucha las solicitudes que llegan a los endpoints. Por ejemplo, si el frontend hace un POST a /api/register, el backend tiene una función para manejar esa solicitud, algo así:

	•	Si estás usando Node.js con Express:

app.post('/api/register', (req, res) => {
    const { username, password } = req.body;
    // Procesa los datos, guarda en la base de datos...
    res.json({ message: "Usuario registrado" });
});


	•	Si usas Python con Flask:

from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/api/register', methods=['POST'])
def register():
    data = request.json
    username = data['username']
    password = data['password']
    # Procesa los datos...
    return jsonify({"message": "Usuario registrado"})



5. CORS (Cross-Origin Resource Sharing):

Una cosa importante al conectar frontend y backend es el CORS, que es una política de seguridad del navegador. Si tu frontend y backend están en dominios distintos (ej. frontend en www.mipagina.com y backend en api.mipagina.com), debes asegurarte de configurar correctamente el CORS en el backend para que permita solicitudes desde el dominio del frontend.

Ejemplo en Express para permitir CORS:

const cors = require('cors');
app.use(cors());  // Esto permite solicitudes desde cualquier dominio

6. WebSockets (para conexiones en tiempo real):

Si necesitas que la comunicación entre el frontend y backend sea en tiempo real (como en aplicaciones de chat o notificaciones en vivo), puedes usar WebSockets. WebSockets permiten que el servidor y el cliente mantengan una conexión abierta para enviar y recibir datos en ambos sentidos en cualquier momento.

Ejemplo con Socket.io:

	•	Frontend:

const socket = io('https://api.misitio.com');
socket.on('mensaje', data => {
    console.log('Nuevo mensaje:', data);
});


	•	Backend:

io.on('connection', socket => {
    socket.emit('mensaje', '¡Bienvenido al chat!');
});



Resumen del flujo de conexión:

	1.	El frontend hace una solicitud HTTP (GET, POST, etc.) usando fetch, Axios, u otro método.
	2.	La solicitud llega al backend (API) que está en un servidor.
	3.	El backend procesa la solicitud, interactúa con la base de datos si es necesario y genera una respuesta.
	4.	El backend envía la respuesta al frontend en formato JSON.
	5.	El frontend recibe los datos y actualiza la interfaz según sea necesario.

---

### En conclusión

La wea trata sobre un intercambio de datos a través de `APIs` y protocolos `HTTP`, con el frontend actuando como el cliente y el backend como el servidor. 
