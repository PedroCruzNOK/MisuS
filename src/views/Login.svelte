<script>
    import {user} from '../stores/User'
    import {navigate} from 'svelte-routing'

    let email =''
    let password= ''

    const procesarFormulario = () =>{   
        if(!email.trim()|| !password.trim()){
            console.log('campos vacios')
            return
        }
        user.setUser({
            email, password
        })
        navigate('/perfil', {replace:true})
    }
</script>

<div>
    <h1>Acceso</h1>
    <form on:submit|preventDefault={procesarFormulario}>
        <input 
            type="email"
            placeholder="Ingresa tu correo"
            bind:value={email}
        >
        <input 
            type="password"
            placeholder="Contraseña"
            bind:value={password}
        >
        <button type="submit">
            Acceder
        </button>
    </form>
</div>