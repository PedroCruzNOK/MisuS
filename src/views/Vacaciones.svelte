<script>
    import {user} from '../stores/User'
    import {onMount} from 'svelte'
    import {navigate} from 'svelte-routing'

    onMount(() =>{
        if(!$user){
            navigate('/login', {replace: true})
        }
    })
    
</script>

<div class="container">
    <h1>vista vacaciones</h1>
</div> 