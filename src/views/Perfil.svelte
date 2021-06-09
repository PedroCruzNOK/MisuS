<script>
    import {user} from '../stores/User'
    import {onMount} from 'svelte'
    import {navigate} from 'svelte-routing'

    console.log($user)
    onMount(() =>{
        if(!$user){
            navigate('/login', {replace: true})
        }
    })
</script>

<div>
    {#if $user}
        <h1>
            Ruta protegida
        </h1>
    {/if}
</div>
