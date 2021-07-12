<script>
    import {user} from '../stores/User'
    import {onMount} from 'svelte'
    import {Link, navigate} from 'svelte-routing'
    import Navbar from '../components/Navbar.svelte'
    import Titulo from '../components/Titulo.svelte'
    import Boton from '../components/Boton.svelte'

    onMount(() =>{
        if(!$user){
            navigate('/login', {replace: true})
        }
    })
    let datos =[];
    const API = "http://localhost:3000/empleados";
    onMount(async () => {
        const response = await fetch(API);
        datos = await response.json();
		
        
    });
    
</script>

<div class="row">
    <Navbar></Navbar>
    
    <div class="origin-top-right absolute right-0 mt-4 mr-5 w-30 rounded-md shadow-lg py-1 bg-white ring-1 ring-black ring-opacity-5" aria-labelledby="mobile-menu" role="menu">
        <Boton urlBoton="/vacaciones" tituloBoton="Nuevo empleado"></Boton>  
    </div>
    <Titulo tituloPrincipal="Empleados" />
    
    <div class="w-auto md:w-5/5 xl:w-5/5  md:ml-40 md:mr-6 mt-6">
		<div id='recipients' class="p-0 mt-2 lg:mt-0 rounded shadow bg-white">
			<table id="example" class="stripe hover" style="width:100%; padding-top: 0.1em;  padding-bottom: 1em;">
				<thead >
					<tr>
						<th data-priority="1">Nombre del Empleado</th>
						<th data-priority="2">Fecha de Nacimiento</th>
						<th data-priority="3">Antiguedad</th>
                        <th data-priority="4">Departamento</th>
                        <th data-priority="5">Informacion personal</th>
                        <th data-priority="6">Factor IMSS</th>
                        <th data-priority="7">SD</th>
                        <th data-priority="8">SDI</th>
                        <th data-priority="9">Estado</th>
						<td data-priority="10">Editar</td>
						<td data-priority="11">Eliminar</td>
					</tr>
				</thead>
				<tbody>
                    {#each datos as dato}
					<tr class="border-gray-500">
                        <td><span style="" class="text-red-500 no-underline hover:text-gray-400">{dato.nombre}</span><br></td>
                        <td class="text-gray-500">{dato.fechaNacimiento}</td>
                        <td>Ingreso: <span style="" class="text-gray-500"> {dato.fechaIngreso}</span><br>Antiguedad: <span style="" class="text-gray-500"> {dato.antiguedad}</span> </td>
                        <td>Departamento: <span style="" class="text-gray-500"> {dato.dependencia}</span><br>Puesto: <span style=""class="text-gray-500"> {dato.areaPuesto}</span> </td>
                        <td>RFC: <span style="" class="text-gray-500"> {dato.RFC}</span> <br>CURP:  <span style="" class="text-gray-500">{dato.CURP}</span><br>NSS: <span style=""class="text-gray-500"> {dato.NSS}</span></td>
                        <td class="text-gray-500">{dato.SD}</td>
                        <td class="text-gray-500">{dato.SDI}</td>
                        <td class="text-gray-500">{dato.estado}</td>
                        <td class="text-gray-500">{dato.empresa}</td>
                        <td ><Link to="/empleados/ver" class="block py-1 md:py-3 pl-1 align-middle text-blue-400 no-underline hover:text-gray-400">
                            <i class="bi bi-pencil pl-2"></i><span class="w-full inline-block pb-1 md:pb-0 text-sm"></span>
                            </Link>
                        </td>
                        
                        <td><Link to="/" class="block py-1 md:py-3 pl-1 align-middle text-red-500 no-underline hover:text-gray-400">
                                <i class="bi bi-trash pl-2"></i><span class="w-full inline-block pb-1 md:pb-0 text-sm"></span>
                            </Link>
                        </td>
					</tr>  

                    {/each}
				</tbody>
			</table>
		</div>
    </div>
</div>

<style>
    td{
        padding-left: 0.7em;
    }
</style>