<template>
  <v-container>
    <v-row>
      <v-col md="4" v-for="project in projects" :key="project.id">
        <v-card>
          <v-card-title>
            {{ project.title }}
          </v-card-title>
          <v-card-actions>
            <v-btn @click="project.showDetails = !project.showDetails">show details</v-btn>
          </v-card-actions>
          <v-expand-transition>
            <div v-show="project.showDetails">
              <v-list>
                <v-subheader>
                  project description
                </v-subheader>
                <v-list-item>
                  description: {{ project.details.description }}
                </v-list-item>
                <v-list-item>
                  size: {{ project.details.size }}
                </v-list-item>
                <v-list-item>
                  upload date: {{ project.details.uploadDate }}
                </v-list-item>
              </v-list>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
      <v-col md='4' >
        <v-card class='addModelButton' @click='modelUpload = !modelUpload'>
          <v-icon
          large
          >
            mdi-gamepad-round
          </v-icon>
        </v-card>
      </v-col>
    </v-row>
    <!-- Model upload form -->
    <v-stepper v-model="e1" v-show="modelUpload">
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
            <v-list-item 
              v-for="(option, i) in currentProject.options"
              :key="i"
            >
              <v-list-item-content>

                <v-file-input
                  v-if="option.type == 'file'"
                  :label="option.label"
                ></v-file-input>
                
                <v-text-field
                  v-if="option.type == 'string'"
                  v-model="option.value"
                  :label="option.label"
                ></v-text-field>

                <v-text-field 
                  v-if="option.type == 'number'"
                  v-model="option.value"
                  type="number"  
                  :label="option.label"
                  @change="countFileInputs"
                ></v-text-field>

                <v-textarea
                  outlined
                  v-if="option.type == 'text'"
                  v-model="option.value"
                  :label="option.label"
                ></v-textarea>

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
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      modelUpload: false,
      e1: 1,
      currentProject: {
        options: [
          {
            label: 'project preview image',
            type: 'file',
            value: ''
          },
          {
            label: 'project title',
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
            value: 1
          }
        ]
      },
      //projectModelCount: 0,
      projects: [
        {
          id: 0,
          title: 'test project',
          showDetails: false, 
          details: {
            size: '100kB',
            uploadDate: '01.01.2021',
            description: 'lorem ipsum dolor sit amet',
          }
        },
        {
          id: 0,
          title: 'test project',
          showDetails: false, 
          details: {
            size: '100kB',
            uploadDate: '01.01.2021',
            description: 'lorem ipsum dolor sit amet',
          }
        },
        {
          id: 0,
          title: 'test project',
          showDetails: false, 
          details: {
            size: '100kB',
            uploadDate: '01.01.2021',
            description: 'lorem ipsum dolor sit amet',
          }
        },
        {
          id: 0,
          title: 'test project',
          showDetails: false, 
          details: {
            size: '100kB',
            uploadDate: '01.01.2021',
            description: 'lorem ipsum dolor sit amet',
          }
        },
      ],
    }
  }
}
</script>

<style lang="css" scoped>

  .addModelButton {
    display: flex;
    align-content: center;
    justify-content: center;
    background: rgba(255, 255, 255, 0.6);
    height: 100%
  }
</style>