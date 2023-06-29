<template>
    <section>
      <portal to="title-toolbar">
        {{ property.name }}
      </portal>
      <v-container>
          <v-row>
              <v-col class="col-12">
                  <v-card class="rounded-lg">
                      <v-img :src="property.image" height="300"></v-img>
                      <v-card-text>
                          <v-row no-gutters class="mb-3">
                              <v-col class="col-8">
                                  <span class="font-weight-bold black--text">Cuota</span>
                              </v-col>
                              <v-col class="col-4 text-right">
                                  <span class="font-weight-bold black--text">4</span>
                              </v-col>
                          </v-row>
                          <v-row no-gutters class="mb-3">
                              <v-col class="col-8">
                                  <span class="font-weight-bold black--text">Cuotas pendientes</span>
                              </v-col>
                              <v-col class="col-4 text-right">
                                  <span class="font-weight-bold black--text">{{ property.pending_installments }}</span>
                              </v-col>
                          </v-row>
                          <v-row no-gutters class="mb-3">
                              <v-col class="col-8">
                                  <span class="font-weight-bold black--text">Proximo vencimiento</span>
                              </v-col>
                              <v-col class="col-4 text-right">
                                  <span class="font-weight-bold black--text">{{ formatDate(property.next_due_date) }}</span>
                              </v-col>
                          </v-row>
  
                      </v-card-text>
                      <v-card-actions class="d-flex justify-center">
                          <v-btn color="secondary" class="font-weight-extra-bold" depressed large rounded>
                              <span class="pa-3 text-capitalize">Ver contrato</span>
                          </v-btn>
                      </v-card-actions>
                  </v-card>
              </v-col>
          </v-row>
      </v-container>
  
    </section>
  </template>
  
  
  <script>
  import properties from '~/static/rentas.json'
  import moment from 'moment'
  export default {
      layout: 'withBackButton',
    data(){
      return {
        properties:properties
      }
    },
    methods:{
        formatDate(date){
            return moment(date).format('DD/MM/YYYY')
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
  