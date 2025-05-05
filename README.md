# 📦 POSTMAIL - API de Gestión de Envíos  
**Repositorio del Parcial 2**  

## 📌 Endpoints  

### 🔹 Crear Usuario con Créditos  
**Método:** POST  
**Ruta:** `/usuario/comprar`  
**Descripción:** Crea un usuario con créditos según el plan seleccionado.  

**Paquetes disponibles:**  
- Paquete 1: 30 envíos ($135)  
- Paquete 2: 40 envíos ($160)  
- Paquete 3: 60 envíos ($180)
(NOTA: para hacer la compra del paquete colocar "30_envios, 40_envios o 60_envios dependiendo de que paquete quisiera el usuario adquirir);

**Ejemplo de cuerpo (JSON):**  
```json
{
  "nombre": "William",
  "paquete": "30_envios"
}
```
**Respuesta esperada:**
```json
{
  "mensaje": "Paquete 30_envios comprado exitosamente"
}
```
### 🔹 Registrar Envío
**Método:** POST  
**Ruta:** `/envio/registrar`  
**Descripción:** Crea un usuario con créditos según el paquete seleccionado.  

**Ejemplo de cuerpo (JSON):**
```json
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
}
```
**Respuesta esperada:**
```json
{
  "mensaje": "Envio registrado con exito"
}
```
### 🔹 Consultar Envíos/Usuario
**Método:** GET  
**Ruta:** `/envios/:nombre`  
**Descripción:** Muestra la informacion del usuario, los creditos actuales, los envios realizados y la informacion de cada envio con su monto de creditos cobrados.

**Ejemplo de peticion:**
`http://localhost:3000/envios/William`

**Respuesta esperada:**
```json
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
```
### 🔹 Eliminar Envío
**Método:** DELETE  
**Ruta:** `/envio/:nombre/:id`  
**Descripción:** Este metodo elimina un envio realizado basandose en el id de este, asimismo reembolsa los creditos gastados en ese envio.

**Ejemplo de peticion:**
`http://localhost:3000/envio/William/ID_del_envio`

**Respuesta esperada:**
```json
{
  "mensaje": "Envío eliminado y créditos devueltos"
  "status": "success"
}
```

# ⚙️ Configuración
**Pasos para probar la API**
**1. Clona el repositorio:** git clone https://github.com/Frederickb9/Parcial2POO.git
**2. Instala dependencias:** npm install express mongoose dotenv
**3. Crea un archivo .env y configura las variables de entorno:** MONGODB_URI=tu_cadena_de_conexion
PORT=3000
**4. Ejecuta el servidor:** node app.js

# 🛠️ Tecnologías Utilizadas
**Node.js**

**Express.js**

**MongoDB**

**Mongoose**

# ✒️ Autor
**Frederick Adrian Benavidez Flores**
