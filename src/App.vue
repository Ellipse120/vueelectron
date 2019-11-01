<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">Live Stream Demo</span>
      </v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-row justify="center" align="center">
        <v-progress-circular
            :rotate="-90"
            :size="100"
            :width="15"
            :value="value"
            color="primary"
        >
          {{ value }}
        </v-progress-circular>
      </v-row>

      <testTable/>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
	import HelloWorld from './components/HelloWorld'
	import TestTable from './components/table'

	const { ipcRenderer } = require('electron')

	export default {
		name: 'App',
		components: {
			HelloWorld,
			TestTable
		},
		data: () => ({
			value: 90
		}),
		mounted () {
			ipcRenderer.on('asynchronous-reply', (event, arg) => {
				console.log(arg)
			})
			ipcRenderer.send('asynchronous-message', 'ping')
		},
    computed: {
    }
	}
</script>
