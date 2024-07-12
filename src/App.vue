<template>
  <CardUser :usuario="usuarios[0]" @enviarMensaje="enviarMensajeHandler" />
  <ChatforTwo :mensajes="mensajes" :usuarios="usuarios"/>
  <CardUser :usuario="usuarios[1]" @enviarMensaje="enviarMensajeHandler" class="usuario1" />
</template>


<script>
import axios from 'axios';
import CardUser from './components/CardUser.vue';
import ChatforTwo from './components/ChatforTwo.vue';


export default {
name: 'App',
components: {
CardUser,
ChatforTwo,
},
data() {
return {
usuarios: [],
mensajes: [],
}
},
methods: {
enviarMensajeHandler(mensaje) {
      let nuevoMensaje = {
          id: mensaje.id,
          color: mensaje.color,
          nombreCompleto: mensaje.nombreCompleto,
          texto: mensaje.texto
      }
      this.mensajes.push(nuevoMensaje)
  }
},
async created() {
try {
  let response = await axios.get("https://randomuser.me/api/?results=2")
  this.usuarios = response.data.results
  console.log(response);

} catch (error) {
  console.log(error)
}
}
}
</script>

<style>
#app {
display: flex;
align-items: stretch;
gap: 2rem;
}
</style>