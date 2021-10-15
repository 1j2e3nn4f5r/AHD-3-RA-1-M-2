

<template>
    <div class="container mt-5">
        <Formulario @filas="DatosTabla"></Formulario>

        <hr>

        <Tabla :FilasTabla="DatosTableHijo"></Tabla>
    </div>
</template>
<script>
import Formulario from '../components/Formulario.vue';
import Tabla from '../components/Tabla.vue';
    export default{
        name : 'Tarea',
        components : {
            Formulario,
            Tabla
        },
        data(){
            return {
                DatosTableHijo:[]
            }
        },
        methods :{
            DatosTabla(valores){
                this.DatosTableHijo = valores;
            }
        }
    }
</script>