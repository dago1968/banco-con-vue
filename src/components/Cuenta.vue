<template>
  <h3>Tipo de Cuenta: {{ tipocuenta }}</h3>
  <h3>Cuenta {{ activa ? 'Activa' : 'Desactivada' }}</h3>
  <h3>Disponible: {{ disponible }}</h3>
  <!--
    <ul>
      <li v-for="(item, index) in servicios" :key="index">    
        {{ index + 1 }} - {{ item }}
      </li>
    </ul>
  -->
  <div v-for="(servicio, index) in servicios" :key="index">
    {{ index + 1}} - {{ servicio }}
  </div>
  <AccionSaldo 
    texto="Adumentar Saldo" 
    @accion="aumentar"
  />
  <AccionSaldo 
    texto="Disminuir Saldo" 
    @accion="disminuir"
    :desactivar="desactivar"

  />
  
</template>

<script>
import AccionSaldo from './AccionSaldo.vue'

export default {
    name: 'Cuenta', 
    components: {
      AccionSaldo
    },  
    data() {
      return {
        tipocuenta: 'visa',
        activa: false,
        disponible: 1000,
        servicios: ['Ahorro', 'Prestamos', 'Credito'],
        desactivar: false
      }
    },
    methods: {
      aumentar() {
        this.disponible= this.disponible + 100;
        this.desactivar = false
      },
      disminuir() {
        if(this.disponible === 0) {
          this.desactivar = true
          alert('Sin Disponible');
          return
        }
        this.disponible = this.disponible - 100;
      }

    }
    


    
    
}
</script>

<style>
  li {
    list-style: none;
  }
</style>