<template>
  <v-container>
    <v-row>
      <v-col class="col-12" v-for="property in properties" :key="property.id">
        <router-link :to="`/rents/single/${property.id}`" tag="div">
          <propertiesCardComponent :property="property"></propertiesCardComponent>
        </router-link>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import rents from '~/static/rentas.json'
export default {
  name: 'IndexPage',
  data(){
    return {
      properties:rents
    }
  }
}
</script>
