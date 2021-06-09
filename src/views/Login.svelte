<script>
    import {user} from '../stores/User'
    import {navigate} from 'svelte-routing'
    import {auth, provider} from '../firebase'

 

    const procesarFormulario = async () =>{     
        try {
            const res = await auth.signInWithPopup(provider)
            console.log(res)
            user.setUser(res.user)
            navigate('/perfil', {replace: true})
        } catch (error) {
            console.log(error)
        }     
        
    }
</script>

<div>
    <h1>Acceso</h1>
    <button type="submit" on:click={procesarFormulario}>
        Acceder Google
    </button>
    
</div>