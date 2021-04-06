<template>
    <button @click="accion" :disabled="desactivate">{{nombre}}</button>
</template>

<script>
export default {
    name:'ModificarSaldo',
    props: {
        nombre: String,
        desactivate: Boolean      
    },
    methods: {
        accion() {
            this.$emit('signal')
        }
    },
}
</script>

<style>

</style>