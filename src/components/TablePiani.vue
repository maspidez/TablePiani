<!-- This program is marvelous -->
<template>
  <div id="TablePianiContainer">
    <v-app id="inspire">
      
      <v-card>
        <v-card-title>
          <h2>Elenco edifici</h2>
          <v-spacer></v-spacer>
          <v-text-field
            v-model="mySearch"
            label="Ricerca"
            append-icon="search"
          ></v-text-field>
        </v-card-title>
        <v-data-table
        :headers="getHeaders"
        :items="getValues"
        :search="mySearch"
        class="elevation-1"
      >
        <template v-slot:items="props">
          <td>{{ props.item.CodiceEdificio }}</td>
          <td class="text-xs-left">{{ props.item.DescrizioneEdificio }}</td>
          <td class="text-xs-left">{{ props.item.LivelloPiano }}</td>
          <td class="text-xs-left"><a href="https://dev.reftree.it" target="_blank">{{ props.item.FILE_NAME }}</a></td>
        </template>
    
          <template v-slot:no-results>
            <v-alert :value="true" color="error" icon="warning">
              Your search for "{{ mySearch }}" found no results.
            </v-alert>
          </template>
        </v-data-table>
      </v-card>
    </v-app>
  </div>
</template>
<script>
import edifJson from '../../edifici.json';
export default {
  data () {
    return {
      myData: edifJson,
      mySearch: '',
      headers: [
        {
          text: 'Dessert (100g serving)',
          align: 'left',
          sortable: false,
          value: 'name'
        },
        { text: 'Calories', value: 'calories' },
        { text: 'Fat (g)', value: 'fat' },
        { text: 'Carbs (g)', value: 'carbs' },
        { text: 'Protein (g)', value: 'protein' },
        { text: 'Iron (%)', value: 'iron' }
      ],
      desserts: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%'
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%'
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%'
        },
        {
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%'
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%'
        },
        {
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: '0%'
        },
        {
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: '2%'
        },
        {
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: '45%'
        },
        {
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%'
        },
        {
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: '6%'
        }
      ]
    }
  }
  ,
computed: {
    getHeaders() {
      var Headers =[];
       for(var i in this.myData.ListaEdifici[0] )
       {
         Headers.push( { text: i, value: i })
         
       }
       return Headers
    },
    getValues(){
      return this.myData.ListaEdifici
    }
}

}
</script>
