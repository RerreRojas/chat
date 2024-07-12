<template>
  <div id="scrollable" class="container">
      <div  v-for="(mensaje, index) in mensajes" :key="index">
          <p :style="
              { textAlign: mensaje.id === usuarios[0].id.value ? 'left' : 'right', marginBottom: 0 , opacity: 0.6, fontSize: '15px' }">
              <small>{{ mensaje.nombreCompleto }}</small>
          </p>
          <p  :style="{

              textAlign: mensaje.id === usuarios[0].id.value ? 'left' : 'right',   color: isDarkColor(mensaje.color) ? 'white' : 'black',}">
              <span  id="texto" :style="{backgroundColor: mensaje.color,}">{{ mensaje.texto }}</span>
              
          </p>
      </div>
  </div>
</template>

<script>
export default {
  name: "ChatforTwo",

  props: {
      mensajes: Array,
      usuarios: Array,
  },
  methods: {
    isDarkColor(color) {
      // Convierte el color a un valor RGB
      const rgb = this.hexToRgb(color);
      if (!rgb) return false;

      // Calcula la luminosidad
      const luminosity = (0.299 * rgb.r + 0.587 * rgb.g + 0.114 * rgb.b) / 255;

      // Devuelve true si el color es oscuro
      return luminosity < 0.5;
    },
    hexToRgb(hex) {
      // Elimina el '#' si está presente
      hex = hex.replace(/^#/, '');

      // Procesa los formatos cortos y largos de hex
      let bigint, r, g, b;
      if (hex.length === 3) {
        bigint = parseInt(hex, 16);
        r = (bigint >> 8) & 255;
        g = (bigint >> 4) & 255;
        b = bigint & 255;
      } else if (hex.length === 6) {
        bigint = parseInt(hex, 16);
        r = (bigint >> 16) & 255;
        g = (bigint >> 8) & 255;
        b = bigint & 255;
      } else {
        return null;
      }

      return { r, g, b };
    }
  }
}

</script>

<style>
#scrollable {
  flex-grow: 2;
  max-height: 80vh;
  overflow-y: scroll;
  background-color: rgb(217, 230, 230);
  height: 67.5vh;
  padding:0 20px;
}
#texto{border-radius: 20px;
  padding: 10px;
  overflow-x: auto;
 

}


</style>