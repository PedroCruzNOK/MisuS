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
<div class="row">
    {#if $user}
    <div class="col-sm-auto bg-light sticky-top">
        <div class="d-flex flex-sm-column flex-row flex-nowrap bg-light align-items-center sticky-top">
            <Link to="/" class="d-block p-3 link-dark text-decoration-none" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Icon-only">
                <i class="bi-bootstrap fs-1"></i>
            </Link>
            <ul class="nav nav-pills nav-flush flex-sm-column flex-row flex-nowrap mb-auto mx-auto text-center align-items-center">
                <li>
                    <Link to="/perfil" class="nav-link py-3 px-2" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Customers">
                        <i class=" bi-person-bounding-box fs-4"></i>
                        PERFIL
                    </Link>
                </li>
                <li>
                    <Link to="/agenda" class="nav-link py-3 px-2" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Customers">
                        <i class="bi bi-journal-bookmark-fill fs-4"></i>
                        AGENDA
                    </Link>
                </li>
                <li>
                    <Link to="/vacaciones" class="nav-link py-3 px-2" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Customers">
                        <i class="bi-people fs-4"></i>
                        VACACIONES
                    </Link>
                </li>
                <li>
                    <Link to="/empleados" class="nav-link py-3 px-2" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Customers">
                        <i class="bi-people fs-4"></i>
                        EMPLEADOS
                    </Link>
                </li>
                <li>
                    <Link to="/ajuste" class="nav-link py-3 px-2" title="" data-bs-toggle="tooltip" data-bs-placement="right" data-bs-original-title="Customers">
                        <i class="bi-people fs-4"></i>
                        AJUSTE
                    </Link>
                </li>
                <li>
                    <button class="btn btn-primary" on:click={cerrarSesion}>Cerrar sesion</button>
                </li>
            </ul>
            
        </div>
    </div>
    {:else}
        <Link to= "/login" class="">LOGIN</Link>
    {/if}

</div>

