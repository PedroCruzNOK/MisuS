<script>
    import {user} from '../stores/User'
    import {onMount} from 'svelte'
    import {navigate} from 'svelte-routing'
import Navbar from '../components/Navbar.svelte'

    console.log($user)
    onMount(() =>{
        if(!$user){
            navigate('/login', {replace: true})
        }
    })
</script>

<div>
    {#if $user}
        <Navbar />
    {/if}
</div>
