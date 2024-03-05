<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>


      <v-list>
          <v-list-item
            prepend-avatar="https://github.com/yurimarcon/avatars/blob/main/Colored/ToyFaces_Colored_BG_59.jpg?raw=true"
            subtitle="To-Do List"
            title="Eduardo Alves"
          >
          </v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list
          :lines="false"
          density="compact"
          nav
        >
          <router-link v-for="(item, i) in items"
            :key="i"
            :to="item.to">

            <v-list-item
            color="primary"
          >
            <template v-slot:prepend>
              <v-icon :icon="item.icon"></v-icon>
            </template>

            <v-list-item-title :textContent="item.text"></v-list-item-title>
          </v-list-item>
        
        </router-link>          
        </v-list>

    </v-navigation-drawer>

    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>To Do List</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'

  const drawer = ref(null)
</script>

<script>

  const items = [
        { text: 'Home', icon: 'mdi-folder', to: '/' },
        { text: 'About', icon: 'mdi-account-multiple', to: '/about' },

      ]
  export default {
    data: () => ({ drawer: null })
    }
  
</script>

<style scoped>
a{
  text-decoration: none;
  color: #505050;
}
</style>