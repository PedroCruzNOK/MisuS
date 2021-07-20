<script>
import {user} from '../stores/User'
import {onMount} from 'svelte'
import {navigate} from 'svelte-routing'

import Tabla from '../components/Tabla.svelte'
    onMount(() =>{
        if(!$user){
            navigate('/login', {replace: true})
        }
    })
</script>

<div>
    {#if $user}
        
        <Tabla />
    {/if}
</div>
