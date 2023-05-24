<script setup>
  import { ref } from 'vue';

  import HelloWorld from './components/HelloWorld.vue'
  import ComponentTest from './components/ComponentTest.vue'
  import Compteur from './components/Compteur.vue'

 
  const a = 1
  const e = ref('')
  const b = ref(0)
  const name = a == 1 ? ref('Mich') : ref('Ayayayaya')
  const squaresMsg = ref('Still place in the area!')

</script>

<template>

	<div class="title">
		<h3>Ceci est la zone de compteur</h3>
		<Compteur :prefix="name"/>
	</div>
	<div>
		<a href="https://vitejs.dev" target="_blank">
			<img src="/vite.svg" class="logo" alt="Vite logo" />
		</a>
		<a href="https://vuejs.org/" target="_blank">
			<img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
		</a>
	</div>
	<h2>Not affected by scoped style</h2>
	<p>{{ b }}</p>
	<p>{{ e }}</p>
	<p>{{ squaresMsg }}</p>
	<ComponentTest @is-finished="(arg1, arg2, arg3) => {
		squaresMsg = arg1,
		e = arg2, 
		b = arg3
	}"/>
	<HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
	height: 6em;
	padding: 1.5em;
	will-change: filter;
	transition: filter 300ms;
}
.logo:hover {
 	filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  	filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
