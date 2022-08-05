<template>
    <app-layout>
        <template #header>
            <h1
                class="text-center text-2xl font-bold leading-7 text-gray-300 sm:text-3xl sm:truncate py-4 bg-gradient-to-l from-indigo-500 to-indigo-800"
            >
                EDITAR ALUMNO
            </h1>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <form @submit.prevent="submit" class="mb-6">
                        <div
                            class="grid grid-cols-1 md:grid-cols-2 gap-5 md:gap-8 mt-5 mx-7"
                        >
                            <div class="grid grid-cols-1">
                                <label
                                    class="uppercase md:text-sm text-xs text-gray-500 text-light font-semibold"
                                    >Nombre</label
                                >
                                <input
                                    id="Nombre"
                                    v-model="form.Nombre"
                                    class="py-2 px-3 rounded-lg border-2 border-purple-300 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent"
                                    type="text"
                                    placeholder="Nombre"
                                />
                            </div>

                            <div class="grid grid-cols-1">
                                <label
                                    class="uppercase md:text-sm text-xs text-gray-500 text-light font-semibold"
                                    >Email</label
                                >
                                <input
                                    id="Email"
                                    v-model="form.Email"
                                    class="py-2 px-3 rounded-lg border-2 border-purple-300 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent"
                                    type="text"
                                    placeholder="Email"
                                />
                            </div>

                            <div class="grid grid-cols-1">
                                <label
                                    class="uppercase md:text-sm text-xs text-gray-500 text-light font-semibold"
                                    >Precio</label
                                >
                                <input
                                    id="NumTel"
                                    v-model="form.NumTel"
                                    class="py-2 px-3 rounded-lg border-2 border-purple-300 mt-1 focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent"
                                    type="text"
                                    placeholder="Telefono"
                                />
                            </div>
                        </div>

                        <div
                            class="flex justify-end md:gap-8 gap-4 pt-5 pb-5 pr-5"
                        >
                            <Link
                                :href="route('alumnos.index')"
                                class="w-auto bg-gray-500 hover:bg-gray-700 rounded-lg shadow-xl font-medium text-white px-4 py-2"
                                type="button"
                            >
                                Cancelar
                            </Link>
                            <button
                                type="submit"
                                class="w-auto bg-purple-500 hover:bg-purple-700 rounded-lg shadow-xl font-medium text-white px-4 py-2"
                            >
                                Guardar
                            </button>
                            <Link
                                        method="delete"
                                        :href="
                                            route('alumnos.destroy', alumno.id)
                                        "
                                        class="flex-shrink-0 bg-pink-500 text-white text-base font-semibold py-2 px-4 rounded-lg shadow-md hover:bg-pink-700 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:ring-offset-2 focus:ring-offset-pink-200"
                                        type="button"
                                    >
                                        Borrar
                                    </Link>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/AppLayout";
import { Link } from "@inertiajs/inertia-vue3";

export default {
  components: {
    AppLayout,
    Link,
  },
  props: ["alumno"],
  data() {
    return {
      form: {
          Nombre: this.$props.alumno.Nombre,
          Email: this.$props.alumno.Email,
          NumTel: this.$props.alumno.NumTel,
      },
    };
  },
  methods: {
    submit() {
      this.$inertia.put(
        route("alumnos.update", this.$props.alumno.id),
        this.form
      );
    },
  },
};
</script>
