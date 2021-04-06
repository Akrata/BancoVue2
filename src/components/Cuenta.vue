<template>
    <div class="container">
        <h2>{{titular}}</h2>
        <hr>
        <h3>Cuenta: {{cuenta}}</h3>
        <h3>Saldo: {{saldo}}</h3>
        <h3>Estado: {{estado ? 'Cuenta Activa' : 'Cuenta Desactivada'}}</h3>
        <h4>Servicios Disponibles</h4>
        <div v-for="(item, index) in transacciones" :key="index">
           {{index+1}}--{{ item }}
        </div>
        <p :hidden="info">Saldo insuficiente</p>
    </div>
    <div>
        <ModificarSaldo @signal="agregarSaldo" class="boton" nombre="Añadir Saldo"></ModificarSaldo>
        <ModificarSaldo :desactivate="desactivar" @signal="disminuirSaldo" class="boton" :class="desactivarBoton"  nombre="Disminuir Saldo"></ModificarSaldo>
    </div>
</template>

<script>
import ModificarSaldo from './ModificarSaldo'
export default {
    name:'Cuenta',
    data() {
        return {
            titular:'Pablo',
            cuenta:'visa',
            saldo: 1000,
            estado: true,
            transacciones:['Deposito','Extraccion', 'Cheques'],
            desactivar:false
        }
    },
    components: {
        ModificarSaldo
    },
    methods: {
        agregarSaldo() {
            this.saldo += 100
            this.desactivar=false
        },
        disminuirSaldo() {
            if(this.saldo === 0){
                this.desactivar = true
                
            }else{
                this.saldo -= 100
            }
            
        }
    },
    computed: {
        desactivarBoton() {
            return this.saldo == 0 ? 'boton-desactivado' :''
        },
        info(){
            return !this.desactivar
        }
    },
   
}
</script>

<style scoped>
    .container{
        border: solid 1px #35495E;
        width: 600px;
        min-height: 500px;
        border-radius:12px;
        position: relative;
    }
    .boton{
        width: 200px;
        height: 50px;
        background: #41B883;
        color: white;
        outline: none;
        border: none;
        margin: 10px;
        border-radius: 12px;
        cursor: pointer;
    }
    .boton-desactivado{
        background: tomato;
        text-decoration:line-through;
        cursor:auto;
    }
    p{
        color: red;
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
    }
    
</style>