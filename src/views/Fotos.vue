<template>
    <div>
       <h1>Galeria de fotos</h1>
      <!--
        En ":to", se pasa un objeto en donde el nombre de la ruta es 'fotos' (creado router.js),
        Luego esto tiene un parametro id llamado id, que se le pasara el item
        osea, reemplazara de la url de esta manera:
        /fotos/item
      -->
      <router-link :to="{ name: 'fotos', params: {id : item} }" v-for=" (item,index) of fotosArreglo" :key="index">
        <button>foto {{item}}</button>
      </router-link>

       <Foto />
      <!-- Usa un metodo para redireccionar a la pagina principal-->
      <button @click="home">HOME</button>
      <!-- Acceso al historial -->
      <button @click="anterior">Anterior</button>
      <button @click="siguiente">Siguiente</button>

    </div>
</template>

<script>
import Foto from '@/components/Fotografia.vue'

export default {
  name: 'Fotos',
  components: {
    Foto
  },
  data () {
    return {
      fotosArreglo: [1, 2, 3]
    }
  },
  methods: {
    home () {
      this.$router.push('/')
    },
    anterior () {
      // Accede al historial para atras
      this.$router.go(-1)
    },
    siguiente () {
      // Accede al historial para adelante
      this.$router.go(1)
    }
  }
}
</script>
