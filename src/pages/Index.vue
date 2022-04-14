<template>
  <div>
    <q-splitter
      v-model="splitterModel"
      style="height: 250px"
    >

      <template v-slot:before>
        <q-tabs
          v-model="tab"
          vertical
          class="text-teal"
        >
          <q-tab name="SWAPI" label="SWAPI" />
          <q-tab name="Vehicles" label="Vehicles" />
          <q-tab name="Starships" label="Starships" />
        </q-tabs>
      </template>

      <template v-slot:after>
        <q-tab-panels
          v-model="tab"
          animated
          swipeable
          vertical
          transition-prev="jump-up"
          transition-next="jump-up"
        >
          <q-tab-panel name="SWAPI">
            <div class="text-h4 q-mb-md">Star Wars API</div>
            <p>Algumas informações dos filmes de Star Wars!</p>
          </q-tab-panel>

          <q-tab-panel name="Vehicles">
            <div class="text-h4 q-mb-md">Vehicles</div>
            <p>name:{{res.results[0].name}};model: {{res.results[0].model}} ;manufacturer: {{res.results[0].manufacturer}} ;cost_in_credits: {{res.results[0].cost_in_credits }} ; length: {{res.results[0].length}} ; crew :{{res.results[0].crew }};
            passengers: {{res.results[0].passengers}}; max_atmosphering_speed: {{res.results[0].max_atmosphering_speed }};
            ;cargo_capacity : {{res.results[0].cargo_capacity }}; consumables  : {{res.results[0].consumables  }} ; films  : {{res.results[0].films  }} ; pilots  : {{res.results[0].pilots  }}
           ; url  : {{res.results[0].url  }}; created   : {{res.results[0].created   }}; edited   : {{res.results[0].edited   }} .</p>
            <li v-for='index in 9' :key='index'>
            <p>name:{{res.results[index].name}};model: {{res.results[index].model}} ;manufacturer: {{res.results[index].manufacturer}} ;cost_in_credits: {{res.results[index].cost_in_credits }} ; length: {{res.results[index].length}} ; crew :{{res.results[index].crew }};
            passengers: {{res.results[index].passengers}}; max_atmosphering_speed: {{res.results[index].max_atmosphering_speed }}
            ;cargo_capacity : {{res.results[index].cargo_capacity }}; consumables  : {{res.results[index].consumables  }} ; films  : {{res.results[index].films  }} ; pilots  : {{res.results[index].pilots  }}
            ; url  : {{res.results[index].url  }}; created   : {{res.results[index].created   }}; edited   : {{res.results[index].edited   }} .</p>
            </li>
          </q-tab-panel>

          <q-tab-panel name="Starships">
            <div class="text-h4 q-mb-md">Starships</div>
             <p>name:{{res.results[0].name}};model: {{res.results[0].model}} ;manufacturer: {{res.results[0].manufacturer}} ;cost_in_credits: {{res.results[0].cost_in_credits }} ; length: {{res.results[0].length}} ; crew :{{res.results[0].crew }};
            passengers: {{res.results[0].passengers}}; max_atmosphering_speed: {{res.results[0].max_atmosphering_speed }};hyperdrive_rating : {{res.results[0].hyperdrive_rating  }};MGLT : {{res.results[0].MGLT  }}
            ;cargo_capacity : {{res.results[0].cargo_capacity }}; consumables  : {{res.results[0].consumables  }} ; films  : {{res.results[0].films  }} ; pilots  : {{res.results[0].pilots  }}
            ; url  : {{res.results[0].url  }}; created   : {{res.results[0].created   }}; edited   : {{res.results[0].edited   }} .</p>
            <li v-for='index in 9' :key='index'>
            <p>name:{{res.results[index].name}};model: {{res.results[index].model}} ;manufacturer: {{res.results[index].manufacturer}} ;cost_in_credits: {{res.results[index].cost_in_credits }} ; length: {{res.results[index].length}} ; crew :{{res.results[index].crew }};
            passengers: {{res.results[index].passengers}}; max_atmosphering_speed: {{res.results[index].max_atmosphering_speed }};hyperdrive_rating : {{res.results[index].hyperdrive_rating  }};MGLT : {{res.results[index].MGLT  }}
            ;cargo_capacity : {{res.results[index].cargo_capacity }}; consumables  : {{res.results[index].consumables  }} ; films  : {{res.results[index].films  }} ; pilots  : {{res.results[index].pilots  }}
            ; url  : {{res.results[index].url  }}; created   : {{res.results[index].created   }}; edited   : {{res.results[index].edited   }} .</p>
            </li>
          </q-tab-panel>
        </q-tab-panels>
      </template>

    </q-splitter>
  </div>
</template>

<script>
import axios from 'axios'
import { ref } from 'vue'
export default {
  data: () => ({
    result: null,
    res: null,
    tab: ref('mails'),

    splitterModel: ref(20)

  }),
  created () {
    axios.get('https://swapi.dev/api/vehicles').then((result) => {
      this.result = result.data
    })
    axios.get('https://swapi.dev/api/starships').then((res) => {
      this.res = res.data
    })
  }
}
</script>

<style scoped lang="scss">
</style>
