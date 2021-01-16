<template>
  <v-container>
    <v-row>
      <v-col v-for="project in projects" :key="project.id">
        <v-card>
          <v-card-title>
            {{ project.title }}
          </v-card-title>
          <v-card-actions>
            <v-btn @click="project.showDetails = !project.showDetails">show details</v-btn>
            <v-btn>Load to VR</v-btn>
          </v-card-actions>
          <v-expand-transition>
            <div v-show="project.showDetails">
              <v-list>
                <v-subheader>
                  project description
                </v-subheader>
                <v-list-item>
                  {{ project.description }}
                </v-list-item>
                <v-subheader>
                  Layers
                </v-subheader>
                <v-list-item v-for="(model, index) in project.models" :key="index">
                  <v-list-item-content>
                     {{ model.type }}
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      projects: [
        {
          id: 0,
          title: 'test project',
          showDetails: false,
          description: 'lorem ipsum dolor sit amet',
          models: [
            {
              type: 'interior',
              path: 'projectId-ModelType'
            },
            {
              type: 'piping',
              path: 'projectId-ModelType'
            },
            {
              type: 'wiring',
              path: 'projectId-ModelType'
            }
          ]
        }
      ]
    }
  }
}
</script>

<style lang="css" scoped>

</style>