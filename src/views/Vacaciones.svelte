<script>
    import {user} from '../stores/User'
    import {onMount} from 'svelte'
    import {navigate} from 'svelte-routing'
import Navbar from '../components/Navbar.svelte'

    onMount(() =>{
        if(!$user){
            navigate('/login', {replace: true})
        }
    })
    
</script>

<div class="row">
    <Navbar />
</div> 