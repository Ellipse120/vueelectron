<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-light">Live Stream Demo</span>
      </v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-row justify="center" align="center" v-if="value !== 'done'">
<!--        <v-progress-circular-->
<!--            :rotate="-90"-->
<!--            :size="100"-->
<!--            :width="15"-->
<!--            :value="value"-->
<!--            color="primary"-->
<!--        >-->
<!--          {{ value }}-->
<!--        </v-progress-circular>-->

        <v-skeleton-loader
            width="100%"
            ref="skeleton"
            :boilerplate="boilerplate"
            :type="type"
            :tile="tile"
            class="mx-auto"
        />
      </v-row>

      <template v-else>
        <testTable/>
        <HelloWorld/>
      </template>
    </v-content>
  </v-app>
</template>

<script>
	import HelloWorld from './components/HelloWorld'
	import TestTable from './components/table'
  import { ipcRenderer } from 'electron'

	export default {
		name: 'App',
		components: {
			HelloWorld,
			TestTable
		},
		data: () => ({
			value: 90,
      boilerplate: false,
      tile: false,
      type: 'table'
		}),
		mounted () {
			ipcRenderer.on('asynchronous-reply', (event, arg) => {
				console.log(arg)
        this.value = arg
			})
			ipcRenderer.send('asynchronous-message', 'ping')
		},
    computed: {
    }
	}
</script>
