<template>
  <ul>
    <li v-for="(img,index) in images"
    :key="index" @click="verImagen(img.id)"><img class="images" :src="img.name"/></li>
  </ul>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  name: 'report-collection',
  computed: {
    ...mapGetters([
      'getReports'
    ]),
    images () {
      return this.getReports
    }
  },
  methods: {
    ...mapActions([
      'getImages'
    ]),
    verImagen (imageId) {
      this.$router.push({name: 'reporte', params: { id: imageId }})
    }
  },
  created () {
    this.getImages()
  }
}
</script>

<style scoped>
  li {
    display:inline;
    float:left;
    width:7rem;
    height:7rem;
    background-color:#f5f7f9;
    margin:3%;
    text-align: center;
    border-right: #a5a7aa solid 1px;
    border-bottom: #a5a7aa solid 1px;
    cursor: pointer;
  }
  .images{
    width:7rem;
    height:7rem;
  }
</style>
