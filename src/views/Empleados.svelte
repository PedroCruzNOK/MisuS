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

<div class="container-fluid">
    <h1>Empleados</h1>
</div>