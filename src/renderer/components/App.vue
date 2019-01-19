<template>
  <v-app dark>
    <v-content>
      <v-container fluid>
        <v-alert :value="true" type="success">{{ message }}</v-alert>
        <v-btn color="success" @click="ping">ping</v-btn>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import { ipcRenderer } from 'electron'

ipcRenderer.on('msg', (event, msg) => {
  alert(msg)
})

export default {
  data() {
    return {
      message: 'hello world',
    }
  },
  methods: {
    ping() {
      ipcRenderer.send('msg', 'ping')
    },
  },
}
</script>

<style lang="scss">
html {
  overflow-y: auto;
}
</style>
