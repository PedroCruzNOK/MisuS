<script>
    import {user} from '../stores/User'
    import {Link, links, navigate} from 'svelte-routing' 
    import {auth} from '../firebase'
import Agenda from '../views/Agenda.svelte'
import Boton from './Boton.svelte'

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
<div class="row">
    {#if $user}
    <div id="sidebar" class="h-screen w-16 menu bg-white text-white px-4 flex items-center nunito static fixed shadow">
        <ul class="list-reset ">
            <li class="my-2 md:my-0">
                <Link to="/" class="block py-1  pl-1  text-gray-600 no-underline hover:text-red-600">
                    <i class="bi bi-house iconMenu"></i>
                    <span class="w-full inline-block pl-1"> Inicio</span>  
                </Link>
            </li>
            <li class="my-2 md:my-0 ">
                <Link to="/perfil" class="block py-1 md:py-3 pl-1 align-middle text-gray-600 no-underline hover:text-red-600">
                    <i class="bi bi-person-badge iconMenu"></i>
                    <span class="w-full inline-block pb-1 md:pb-0 pl-1"> Perfil</span>
                </Link>
            </li>
            <li class="my-2 md:my-0">
                <Link to="/agenda" class="block py-1 md:py-3 pl-1 align-middle text-gray-600 no-underline hover:text-red-600">
                    <i class="bi bi-journal-bookmark-fill iconMenu"></i>
                    <span class="w-full inline-block pb-1 md:pb-0 pl-1"> Agenda</span>
                </Link>
            </li>
            <li class="my-2 md:my-0">
                <Link to="/empleados" class="block py-1 md:py-3 pl-1 align-middle text-gray-600 no-underline hover:text-red-600">
                    <i class="bi bi-person-check iconMenu"></i> 
                    <span class="w-full inline-block pb-1 md:pb-0 pl-1"> Empleados </span>
                </Link>
            </li>
            <li class="my-2 md:my-0">
                <Link to="/vacaciones" class="block py-1 md:py-3 pl-1 align-middle text-gray-600 no-underline hover:text-red-600">
                    <i class="bi bi-tsunami iconMenu"></i>
                    <span class="w-full inline-block pb-1 md:pb-0 pl-1">Vacaciones </span>
                </Link>
            </li>
            <li class="my-2 md:my-0">
                <Link to="/ajuste" class="block py-1 md:py-3 pl-1 align-middle text-gray-600 no-underline hover:text-red-600">
                    <i class="bi bi-newspaper iconMenu"></i>
                    <span class="w-full inline-block pb-1 md:pb-0 pl-1"> Ajuste </span>
                </Link>
            </li>
            
               
            
        </ul>
    </div>

    <div class="flex flex-row flex-wrap flex-1 flex-grow content-start pl-16">
        <div class="h-40 lg:h-20 w-full flex flex-wrap"> 
            <nav id="header1" class="bg-gray-100 w-auto flex-1 border-b-1 border-gray-300 order-1 lg:order-2">
                <div class="flex h-full justify-between items-center">
                    <div class="relative  max-w-3xl px-6 ml-7">
                        <div class="h-10 mt-0 left-3 top-0 flex items-center ml-10 rounded-md shadow-lg py-1 bg-white ring-1 ring-black ring-opacity-5">
                            <Boton tituloBoton="Actualizar antiguedad" />                       
                        </div>
                    </div>
                    <br>
                    <div class="flex relative inline-block pr-6">
                        <div class="relative text-sm">
                            <button  class="btn-indigo flex items-center focus:outline-none mr-3">
                                <img class="w-8 h-8 rounded-full mr-4" src="http://i.pravatar.cc/300" alt="Avatar of User">
                                <span class="hidden md:inline-block"> Hola!: {$user.displayName}</span>
                                <button class="btn-red flex items-center" on:click={cerrarSesion}><i class="pl-3 bi bi-x-lg text-red-500 iconMenu"></i></button>
                                
                            </button>
                            
                        </div>
                    </div>
                </div>
            </nav>
        </div>
    </div>
    {:else}
        <Link to= "/login" class="">LOGIN</Link>
    {/if}

</div>

<style>


#sidebar {
    transition: ease-in-out all .3s;
    z-index: 9999;
}

#sidebar span {
    opacity: 0;
    position: absolute;
    transition: ease-in-out all .6s;
}

#sidebar:hover {
    width: 150px;
    box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
    /*shadow-2xl*/
}

#sidebar:hover span {
    opacity: 1;
}

.iconMenu{
    font-size: 22px;
}

/*Row Hover*/

</style>