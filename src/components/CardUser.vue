<template>
    <div class="card">
        <img :src="usuario.picture.large" alt="...">
        <div class="card-body">
            <h5 class="card-title text-center">{{ nombreCompleto }}</h5>
            <form action="">
                <p class="card-body-color">Selecciona el fondo de tu texto</p>
                <input class="form-control mb-2" type="color" name="color" id="color" v-model="mensaje.color">
                <textarea class="form-control" name="chat" id="chat" v-model="mensaje.texto"
                    @keyup.enter="enviarMensaje"></textarea>
                <button @click.prevent="enviarMensaje" class="btn btn-primary my-2">Enviar</button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardUser',
    props: {
        usuario: Object,
    },
    data() {
        return {
            mensaje: {
                texto: "",
                color: "",
                id: "",
            },

        }
    },
    computed: {
        nombreCompleto() {
            return `${this.usuario.name.first} ${this.usuario.name.last}`;
        }
    },
    methods: {
        enviarMensaje() {
            this.mensaje.id = this.usuario.id.value;
            this.mensaje.nombreCompleto = this.nombreCompleto;
            this.$emit("enviarMensaje", this.mensaje)
            this.mensaje.texto = "";
        }
    },
    created() {
        console.log(this.usuario)
    }

}
</script>

<style>
.card {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
}

.card-body {
    background-color: white;
}

.card-body-color {
    font-size: 12px;
}

textarea {
    background-color: v-bind(mensaje.color);
}
</style>