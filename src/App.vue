<template>
	<v-app>
		<v-app-bar app>
			<v-toolbar-title class="headline text-uppercase">
				<span class="font-weight-light">Live Stream Demo</span>
			</v-toolbar-title>
		</v-app-bar>

		<v-content>
			<testTable/>
			<HelloWorld/>
		</v-content>
	</v-app>
</template>

<script>
	import HelloWorld from './components/HelloWorld';
	import testTable from './components/table'

	export default {
		name: 'App',
		components: {
			HelloWorld,
			testTable
		},
		data: () => ({
			//
		}),
	};
</script>
