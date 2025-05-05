# 📦 POSTMAIL - API de Gestión de Envíos  
**Repositorio del Parcial 2**  

## 📌 Endpoints  

### 🔹 Crear Usuario con Créditos  
**Método:** POST  
**Ruta:** `/usuario/comprar`  
**Descripción:** Crea un usuario con créditos según el plan seleccionado.  

**Paquetes disponibles:**  
- Plan 1: 30 envíos ($135)  
- Plan 2: 40 envíos ($160)  
- Plan 3: 60 envíos ($180)  

**Ejemplo de cuerpo (JSON):**  
```json
{
  "nombre": "Rodolfo",
  "paquete": "30_envios"
}

**Respuesta esperada (JSON):** 
{
  "mensaje": "Paquete 30_envios comprado exitosamente"
}

🔹 Registrar Envío
Método: POST
Ruta: /envio/registrar
Descripción: Registra un envío asociado a un usuario.

Ejemplo de cuerpo:

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

