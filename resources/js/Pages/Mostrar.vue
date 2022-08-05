<template>
    <app-layout>
        <h1
            class="text-center text-2xl font-bold leading-7 text-gray-300 sm:text-3xl sm:truncate py-4 bg-gradient-to-l from-indigo-500 to-indigo-800"
        >
            ALUMNOS
        </h1>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <Link
                    :href="route('alumnos.create')"
                    class="flex-shrink-0 bg-blue-500 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 focus:ring-offset-blue-200"
                    type="button"
                >
                    Nuevo
                </Link>

                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <table
                        class="rounded-t-lg mt-3 min-w-full mx-auto bg-gray-800 text-gray-100"
                    >
                        <thead>
                            <tr class="text-center border-b border-gray-300">
                                <th
                                    scope="col"
                                    class="px-6 py-2 text-center text-xs font-medium text-gray-100 uppercase tracking-wider"
                                >
                                    NOMBRE
                                </th>
                                <th
                                    scope="col"
                                    class="px-6 py-2 text-center text-xs font-medium text-gray-100 uppercase tracking-wider"
                                >
                                    EMAIL
                                </th>
                                <th
                                    scope="col"
                                    class="px-6 py-2 text-center text-xs font-medium text-gray-100 uppercase tracking-wider"
                                >
                                    TELEFONO
                                </th>
                            </tr>
                        </thead>
                        <tbody
                            class="bg-gray-700 border-b border-gray-600 text-gray-200"
                        >
                            <tr v-for="alumno in alumnos" :key="alumno.id">
                                <Link class="tbA" :href="route('alumnos.edit', alumno.id) ">
                                <div class="grid grid-cols-3 gap-6 place-items-center h-25 ... py-2 px-4 ">
                                <td>
                                    <div class="">
                                    {{ alumno.Nombre }}
                                    </div>
                                </td>
                                <td>
                                   <div class="">
                                    {{ alumno.Email }}
                                    </div>
                                   
                                </td>
                                <td >
                                   <div class="">
                                   {{ alumno.NumTel }}
                                   </div>
                                </td>
                                </div>
                                <!-- <td class="flex m-4">
                                    <Link
                                        :href="route('alumnos.edit', alumno.id)"
                                        class="flex-shrink-0 bg-purple-600 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-offset-2 focus:ring-offset-purple-200"
                                        type="button"
                                    >
                                        Editar
                                    </Link>
                                    
                                </td> -->
                            </Link>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import { Link } from "@inertiajs/inertia-vue3";
import { Inertia } from "@inertiajs/inertia";
export default {
    name: "Mostrar",

    props: {
        alumnos: Array,
    },
    components: {
        AppLayout,
        Link,
        Inertia,
    },
};
</script>

<style>
.tbA{
    position: relative;
    float: right;
    background-color:red ;
    width: 77em;
    
}
</style>
