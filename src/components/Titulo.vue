<template>
  <h1>{{texto}}</h1>
  
</template>

<script>
export default {
    data() {
        return {
            titulo: "",
        }
    },
    props: {
        texto: String
    }
}
</script>

<style scoped>
    h1{
        color: white;
        text-shadow: 2px 2px #35495E;
        background: #41B883;
        width: 500px;
        padding: 10px;
        border-radius: 8px;
        box-shadow: 4px 4px #35495E;
        letter-spacing: 2px;
    }
</style>