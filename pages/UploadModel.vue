<template>
	<v-stepper v-model="e1">
    <v-stepper-header>
      <v-stepper-step
        :complete="e1 > 1"
        step="1"
      >
        Project options
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step
        :complete="e1 > 2"
        step="2"
      >
        Upload models
      </v-stepper-step>

      <v-divider></v-divider>

      <v-stepper-step step="3">
        Progress
      </v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-list>
          <v-subheader>
            choose project options
          </v-subheader>
          <v-list-item v-for="(option, i) in currentProject.options" :key="i">
            <v-list-item-content>
              <v-text-field  v-if="option.type == 'string'" v-model="option.value" :label="option.label"></v-text-field>
              <v-text-field 
                v-if="option.type == 'number'"
                v-model="option.value" type="number"  
                :label="option.label"
                @change="countFileInputs"
              ></v-text-field>
              <v-textarea outlined v-if="option.type == 'text'" v-model="option.value" :label="option.label"></v-textarea>
            </v-list-item-content>
          </v-list-item>
        </v-list>

        <v-btn
          color="primary"
          @click="e1 = 2"
        >
          Continue
        </v-btn>

        <v-btn text>
          Cancel
        </v-btn>
      </v-stepper-content>

      <v-stepper-content step="2">
        <v-file-input></v-file-input>

        <v-btn
          color="primary"
          @click="e1 = 3"
        >
          Continue
        </v-btn>

        <v-btn text>
          Cancel
        </v-btn>
      </v-stepper-content>

      <v-stepper-content step="3">
        <v-card
          class="mb-12"
          color="grey lighten-1"
          height="200px"
        ></v-card>

        <v-btn
          color="primary"
          @click="e1 = 1"
        >
          Continue
        </v-btn>

        <v-btn text>
          Cancel
        </v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
	data () {
		return {
      e1: 1,
      currentProject: {
        options: [
          {
            label: 'project name',
            type: 'string',
            value: ''
          },
          {
            label: 'project description',
            type: 'text',
            value: ''
          },
          {
            label: 'model count',
            type: 'number',
            value: 0
          }
        ]
      },
      projectModelCount: 0
		}
	},
	mounted() {
		
  },
  methods : {
    countFileInputs: function () {
      
    }
  }
})
</script>

<style lang="css" scoped>
  
</style>