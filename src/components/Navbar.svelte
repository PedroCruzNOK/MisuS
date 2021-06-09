<script>
    import {user} from '../stores/User'
    import {Link, navigate} from 'svelte-routing' 

    const cerrarSesion = () => {
        user.setUser(null)
        navigate('/login', {replace:true})
    }
</script>

<nav>
    {#if $user}
        <Link to= "/perfil">PERFIL</Link>
        <button on:click={cerrarSesion}>Cerrar sesion</button>
    {:else}
        <Link to= "/">HOME</Link>
        <Link to= "/login">LOGIN</Link>
    {/if}
</nav>