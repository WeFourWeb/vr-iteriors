<template>
  <v-app>
    <v-card>
      <v-navigation-drawer
        permanent
        expand-on-hover
        app
      >
        <v-list>
          <v-list-item class="px-2">
            <v-list-item-avatar>
              <v-img src="https://randomuser.me/api/portraits/women/85.jpg"></v-img>
            </v-list-item-avatar>
          </v-list-item>

          <v-list-item link>
            <v-list-item-content>
              <v-list-item-title class="title">
                Current User
              </v-list-item-title>
              <v-list-item-subtitle>user.email@gmail.com</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list
          nav
          dense
        >
          <v-list-item nuxt to="myModels">
            <v-list-item-icon>
              <v-icon>mdi-folder</v-icon>
            </v-list-item-icon>
            <v-list-item-title >My projects</v-list-item-title>
          </v-list-item>
          <v-list-item nuxt to="uploadModel">
            <v-list-item-icon>
              <v-icon>mdi-gamepad-round</v-icon>
            </v-list-item-icon>
            <v-list-item-title >Create new project</v-list-item-title>
          </v-list-item>
          <v-list-item nuxt to="Settings">
            <v-list-item-icon>
              <v-icon>mdi-cog</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-card>
    <v-container>
      <nuxt/>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data () {
    return {

    }
  }
}
</script>

<style lang="css" scoped>

</style>
