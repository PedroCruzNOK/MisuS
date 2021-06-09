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
<div class="container">
    <nav>
        {#if $user}
            <Link to= "/perfil" class="">PERFIL</Link>
            <Link to= "/agenda" class="">AGENDA</Link>
            <button class="btn btn-primary" on:click={cerrarSesion}>Cerrar sesion</button>
        {:else}
            <Link to= "/" class="">HOME</Link>
            <Link to= "/login" class="">LOGIN</Link>
        {/if}
    </nav>
</div>
