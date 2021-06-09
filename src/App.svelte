<script>
	import {Router, Link, Route} from "svelte-routing";
	import Home from './views/Home.svelte'
	import Perfil from './views/Perfil.svelte'
	import Login from './views/Login.svelte'
	import Agenda from './views/Agenda.svelte'
	import Navbar from './components/Navbar.svelte'
	import {onMount} from 'svelte'
	import {user} from './stores/User'

	onMount(async() =>{
		await user.current()
	})
</script>

{#if $user === false}
	<h1>Cargando ...</h1>
{:else}
	<div>
		<h1 class="display-5">Hola bienvenida</h1>
		<Router>
			<Navbar></Navbar>
			<Route path="/">
				<Home></Home>
			</Route>
			<Route path="/perfil">
				<Perfil></Perfil>
			</Route>
			<Route path="/login">
				<Login></Login>
			</Route>
			<Route path="/agenda">
				<Agenda />
			</Route>
		</Router>
	</div>
{/if}


<style>
	

	h1 {
		color: #00bfc5;
		
	}
</style>