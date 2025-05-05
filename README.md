# Proyecto POSTMAIL - API para gestioon de envíos.
Repositorio del parcial 2

Endpoints de la API
1. Crear un usuario con créditos según el plan
Método: POST
Ruta: /usuario/comprar
Descripción: Crea un nuevo usuario asignándole créditos según el plan que elija.
Paquetes disponibles:
Plan 1: 30 envíos por $135
Plan 2: 40 envíos por $160
Plan 3: 60 envíos por $180

Ejemplo de cuerpo (JSON):

{
  "nombre": "Rodolfo",
  "paquete": "30_envios"
}

Respuesta esperada:

{
  "mensaje": "Paquete 30_envios comrpado exitosamente"
}

2. Registrar un envio en el usuario
Método: POST
Ruta: /envio/registrar
Descripción: Registra un envio a nombre del usuario previamente creado, que se almacenara como un subdocumento en el registro del usuario.

Ejemplo del cuerpo:
{
  "nombre": "William",
  "envio": {
    "destinatario": "Carlos",
    "telefono": "7777-8888",
    "direccion": "Calle El Progreso #123",
    "referencia": "Frente a la iglesia",
    "observacion": "Entregar antes de las 5 PM"
  },
  "producto": {
    "descripcion": "Caja de libros",
    "peso": 9,
    "bultos": 1,
    "fecha_entrega": "2025-05-10"
  }

  Respuesta esperada: 
  {
    "mensaje": "Envio registrado con exito"
  }

3. Consultar los envios/informacion del usuario
Método: GET
Ruta: /envios/:nombre
Descripcion: Este metodo muestra la informacion del usuario, los creditos disponibles y los envios registrados con su informacion y el credito que gasto cada uno.

Ejemplo de la peticion:
http://localhost:3000/envios/William

Respuesta esperada:
{
  "_id": "68190dc343be6ea82d94bd92",
  "nombre": "William",
  "__v": 0,
  "creditos": 27,
  "envios": [
    {
      "producto": {
        "descripcion": "Caja de libros",
        "peso": 9,
        "bultos": 1,
        "fecha_entrega": "2025-05-10"
      },
      "destinatario": "Carlos",
      "telefono": "Calle el Progreso",
      "direccion": "77778888",
      "referencia": "Frente a la iglesia",
      "observacion": "Entregar antes de las 5 PM",
      "creditos_usados": 3,
      "_id": "68190e0874698406cabcb5b4"
    }
  ]
}

4. Eliminar un envio
Método: DELETE
Ruta: /envio/:nombre/:id
Descripcion: Este metodo delete eliminara el envio basandose en el ID de este mismo, seran reembolsados la cantidad de creditos gastados en ese envio.

Ejemplo de la peticion:
http://localhost:3000/envio/William/ID del envio realizado

Respuesta esperada:
{
  "mensaje": "Envio eliminado y creditos reembolsados",
  "status": "success"
}

# ¿Cómo ejecutar el proyecto?

1. Clona este repositorio:
   git clone https://github.com/Frederickb9/Parcial2POO.git
2. Instala las dependencias
   npm install express mongoose dotenv
3. Configura las variables de entorno: Crea un archivo .env en la raiz del proyecto y agrega tus credenciales de MongoDB y otras configuraciones necesarias.
4. Ejecuta el servidor
   en la terminal escribe "node app.js" sin las comillas para que el servidor empiece a correr.
5. Prueba la API usando herramientas como ThundereClient o Postman para hacer pruebas con los endpoints.

# Tecnologias utilizadas
  Node.js
  Express.js
  MongoDB
  Mongoose

# Autor
Frederick Adrian Benavidez Flores
