<template>
  <v-container>
    <v-row>
      <v-col class="col-12" v-for="property in properties" :key="property.id">
        <router-link :to="`/properties/single/${property.id}`" tag="div">
          <propertiesCardComponent :property="property"></propertiesCardComponent>
        </router-link>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import properties from '~/static/properties.json'
export default {
  name: 'IndexPage',
  data(){
    return {
      properties:properties
    }
  }
}
</script>
