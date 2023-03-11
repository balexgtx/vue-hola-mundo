<template>
  <div>
    <h1>Cuenta</h1>
    <h2>Tipo de Cuenta: {{ cuenta }}</h2>
    <h2>Saldo: {{ saldo }}</h2>
    <h2>Estado: {{ estado ? 'Activa' : 'Desactivada' }}</h2>
    <ul>
        <li v-for="(servicio, index) in servicios" :key="index">{{servicio}}</li>
    </ul>
    <AccionSaldo
    texto="Aumentar Saldo"
    @accion="aumentar"/>
    <AccionSaldo
     texto="Disminuir Saldo"
     @accion="disminuir" :disabled="activo"/>
  </div>
</template>

<script>
import AccionSaldo from './AccionSaldo.vue';
export default {
    components: {
        AccionSaldo,
    },
  data() {
    return {
      saldo: 1000,
      cuenta: "Visa",
      estado: 'Activa',
      servicios: ['Retiro', 'Deposito', 'Cheque', 'Transferencia'],
      activo: false
    };
  },
  methods: {
    aumentar(){
        this.activo = false
        this.saldo = this.saldo + 100;
    },
    disminuir(){
        if(this.saldo <= 0){
            alert('Saldo Agotado');
            this.activo = true
            return
        }
        this.saldo = this.saldo - 100;
    }
  },
};
</script>

<style>
</style>