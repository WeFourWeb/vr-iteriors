<template>
  <v-container>
    <v-row>
      <v-col max-width="100" v-for="project in projects" :key="project.id">
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
          details: {
            size: '100kB',
            uploadDate: '01.01.2021',
            description: 'lorem ipsum dolor sit amet',
          }
        }
      ],
    }
  }
}
</script>

<style lang="css" scoped>

</style>