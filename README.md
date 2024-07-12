# Dos personas chateando

## Descripción
Este proyecto es una aplicación Vue.js que simula un chat para dos usuarios. La aplicación carga dos usuarios aleatorios desde una API y permite que ambos envíen mensajes que se muestran en un componente de chat.

### Estructura del Proyecto
La estructura del proyecto se compone de los siguientes componentes:

* CardUser: Un componente que muestra la información de un usuario y permite enviar mensajes.
* ChatforTwo: Un componente que muestra los mensajes enviados entre los dos usuarios.

### Código Principal
El template define la estructura de la aplicación con dos componentes CardUser y un componente ChatforTwo en el medio.
* Importaciones: Se importan axios para realizar peticiones HTTP y los componentes CardUser y ChatforTwo.
*  Métodos:
       - enviarMensajeHandler: Este método maneja los mensajes enviados por los usuarios y los agrega a la lista de mensajes.
       
* Datos: La aplicación mantiene dos listas en su data(): usuarios y mensajes.
     
* Ciclo de Vida:  _created: Este hook se ejecuta cuando la instancia del componente es creada y realiza una petición HTTP para obtener dos usuarios aleatorios desde la API https://randomuser.me/api.


