


### ¿Para qué sirve un DTO?

> Data Transfer Object

La finalidad de un DTO es **transferir datos de manera eficiente y estructurada** entre diferentes partes de un sistema, por ejemplo:
- Entre el backend y el frontend de una aplicación.
- Entre capas internas de una aplicación, como la capa de negocio y la capa de presentación.

### ¿Por qué no simplemente usar un objeto común o un modelo de base de datos?

Usar un DTO tiene algunas ventajas importantes:

1. **Controlar los datos que se envían y reciben**:
   - Un DTO permite definir exactamente qué datos se van a transferir. Por ejemplo, si un objeto en la base de datos tiene 20 campos, pero solo necesitas 5 para una operación, el DTO te permite especificar solo esos 5. Esto mejora la eficiencia y evita exponer datos sensibles innecesariamente.

2. **Desacoplar el modelo de la base de datos de la lógica de negocio**:
   - Los modelos que usas en tu base de datos pueden cambiar con el tiempo. Si usas los mismos modelos para transferir datos en la aplicación, esos cambios afectarán a todas las capas que los usan. Con un DTO, puedes mantener una interfaz estable para transferir datos, independientemente de los cambios en el modelo de datos subyacente.

3. **Facilitar la validación de datos**:
   - Los DTO pueden usarse para validar que los datos enviados o recibidos cumplan ciertos requisitos (por ejemplo, que un campo de correo electrónico tenga un formato válido).

4. **Estandarizar la estructura de los datos**:
   - Cuando una aplicación necesita enviar o recibir datos de una API, el DTO asegura que los datos tengan una estructura clara y predecible.

### Ejemplo sencillo para entenderlo mejor

Imagina que tienes un sistema de usuarios, y cada usuario tiene mucha información almacenada en la base de datos, como:

```json
{
    "id": 1,
    "email": "usuario@example.com",
    "password": "hashedpassword",
    "nombre": "Juan",
    "apellido": "Pérez",
    "fecha_nacimiento": "1990-01-01",
    "direccion": "Calle Falsa 123",
    "telefono": "1234567890",
    "rol": "admin",
    "fecha_creacion": "2024-01-01",
    "fecha_actualizacion": "2024-10-10"
}
```

Supongamos que quieres mostrar solo el nombre, apellido y rol en la interfaz. Si envías todo el objeto directamente, estás exponiendo datos que no son necesarios, como el `password`, `direccion`, o `fecha_creacion`.

Aquí es donde un DTO ayuda: puedes crear un DTO que solo incluya los datos necesarios para esta operación:

```typescript
// DTO para mostrar datos del usuario en la interfaz
interface UserDTO {
    nombre: string;
    apellido: string;
    rol: string;
}
```

Y luego usar este DTO para enviar solo esos datos:

```typescript
const userDTO: UserDTO = {
    nombre: "Juan",
    apellido: "Pérez",
    rol: "admin"
};
```

### Resumiendo

- **El DTO actúa como un "filtro" o "molde"** para especificar qué datos se van a transferir y en qué formato.
- **Simplifica la comunicación entre distintas partes del sistema** al ofrecer una interfaz clara para los datos.
- **Reduce riesgos de seguridad** al no exponer datos sensibles o innecesarios.

Usar DTOs hace que el código sea más mantenible, seguro y fácil de entender porque te permite separar la lógica de transferencia de datos de la lógica interna del sistema. 
