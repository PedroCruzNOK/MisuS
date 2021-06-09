<script>
    import {user} from '../stores/User'
    import {Link, navigate} from 'svelte-routing' 
    import {auth} from '../firebase'

    const cerrarSesion = async() => {
        try {
            await auth.signOut()
            user.setUser(null)
            navigate('/login', {replace:true})
        } catch (error) {
            console.log(error)
        }
       
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