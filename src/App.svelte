<script>
	import {Router, Link, Route} from "svelte-routing";
	import Home from './views/Home.svelte'
	import Perfil from './views/Perfil.svelte'
	import Login from './views/Login.svelte'
	import Navbar from './components/Navbar.svelte'
</script>

<div>
	<h1>Hola bienvenida</h1>
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
	</Router>
</div>

<style>
	

	h1 {
		color: #00bfc5;
		
	}
</style>