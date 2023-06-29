<template>
  <section>
    <portal to="title-toolbar">
      {{ property.name }}
    </portal>
    <v-container>
        <v-row no-gutters>
            <v-col class="col-12">
                <h3 class="font-weight-ectra-bold black--text ">Estado de la promocion</h3>
            </v-col>
            <v-col class="col-12">
                <v-progress-linear height="20" color="secondary" class="rounded-xl" rounded :value="property.percent_promotion"></v-progress-linear>
            </v-col>
            <v-col class="col-4">
                <span class="text-subtitle-2 font-weight-bold">Planos</span>
            </v-col>
            <v-col class="col-4 text-center">
                <span class="font-weight-bold secondary--text text-subtitle-2">Licencia de obra</span>
            </v-col>
            <v-col class="col-4 text-right primary--text font-weight-bold">
                Fin
            </v-col>
        </v-row>
        <v-row>
            <v-col class="col-12">
                <v-card class="rounded-lg">
                    <v-img :src="property.image" height="300"></v-img>
                    <v-card-text>
                        <v-row no-gutters class="mb-3">
                            <v-col class="col-8">
                                <v-chip small class="font-weight-bold black--text">Promocion {{ property.promotion_code }}</v-chip>
                            </v-col>
                            <v-col class="col-4 text-right">
                            </v-col>
                        </v-row>
                        <v-divider></v-divider>
                        <v-row no-gutters class="my-3">
                            <v-col class="col-8">
                                <span class="font-weight-bold black--text">{{ property.building_name }}</span>
                            </v-col>
                            <v-col class="col-4 text-right">
                            </v-col>
                        </v-row>
                        <v-divider></v-divider>
                        <v-row no-gutters class="mb-3">
                            <v-col class="col-8">
                                <span class="font-weight-bold black--text">{{ property.area_m2 }} m2</span>
                            </v-col>
                        </v-row>

                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>

  </section>
</template>


<script>
import properties from '~/static/properties.json'
export default {
    layout: 'withBackButton',
  data(){
    return {
      properties:properties
    }
  },
  computed:{
    property(){
        const property = this.properties.find((p)=>{
            return p.id === parseInt(this.$route.params.id)
        })
        return property
    }
  }
}
</script>
