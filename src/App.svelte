<script>
	import {Router, Link, Route} from "svelte-routing";
	import Home from './views/Home.svelte'
	import Perfil from './views/Perfil.svelte'
	import Login from './views/Login.svelte'
	import Agenda from './views/Agenda.svelte'
	import Vacaciones from './views/Vacaciones.svelte'
	import Empleados from './views/Empleados.svelte'
	import AjusteAnual from './views/AjusteAnual.svelte'
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
			<Route path="/">
				<Home />		
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
			<Route path="/vacaciones">
				<Vacaciones />
			</Route>
			<Route path="/empleados">
				<Empleados />
			</Route>
			<Route path="/ajuste">
				<AjusteAnual />
			</Route>
		</Router>
	</div>
{/if}


<style>
	

	h1 {
		color: #00bfc5;
		
	}
</style>