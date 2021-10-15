<template>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-6">
                <label for="Titulo">Titulo</label>
                <input  v-model="Titulo" type="text" class="form-control">
            </div>
            <div class="col-md-6">
                <label for="Titulo">Encargado</label>
                <select v-model="Encargado" class="form-control">
                    <option value="" disabled selected>Elige un Encargado</option>
                    <option v-for="Dato, index in Encargados" :key="index" :value="Dato.id">
                        {{ Dato.nombre }}&nbsp;{{ Dato.apellido }}
                    </option>
                </select>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-md-4">
                <label for="Titulo">Depositos</label>
                <select v-model="Deposito" class="form-control">
                    <option value="" disabled selected>Elige un Depósito</option>
                    <option v-for="Dato, index in Depositos" :key="index" :value="Dato.id">
                        {{ Dato.descripcion }}
                    </option>
                </select>
            </div>
            <div class="col-md-4">
                <label for="Titulo">Progresos</label>
                <select v-model="Progreso" class="form-control">
                    <option value="" disabled selected>Elige un Progreso</option>
                    <option v-for="Dato, index in Progresos" :key="index" :value="Dato.id">
                        {{ Dato.descripcion }}
                    </option>
                </select>
            </div>
            <div class="col-md-4">
                <label for="Titulo">Prioridades</label>
                <select v-model="Prioridad" class="form-control">
                    <option value="" disabled selected>Elige una Prioridad</option>
                    <option v-for="Dato, index in Prioridades" :key="index" :value="Dato.id">
                        {{ Dato.descripcion }}
                    </option>
                </select>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-md-4">
                <label for="">Fecha de Inicio</label>
                <input v-model="FechaInicio" type="date" class="form-control">
            </div>
            <div class="col-md-4">
                <label for="">Fecha de Vencimiento</label>
                <input v-model="FechaVencimiento" type="date" class="form-control">
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-md-6">
                <label>Notas</label>
                <textarea v-model="Notas" rows="2" class="form-control" placeholder="Escriba una descripción o agregue notas aquí"></textarea>
            </div>
        </div>
        <div class="row mt-3">
            <div class="col-md-12">
                <label for="">Lista Comprobacion</label>
            </div>
            <div class="row mt-3 justify-content-md-end">
                <div class="col-md-2 g-grid">
                    <button class="btn btn-primary mb-2 regular-button" @click="GuardarTarea()">Guardar</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
   name : 'Formulario',
   data(){
       return{
           Encargados : [
                {
                   id : 1,
                   nombre : 'Pancho',
                   apellido : 'Riado' 
                },
                {
                   id : 1,
                   nombre : 'Maria',
                   apellido : 'Díaz' 
                }
            ],
           Depositos : [
               {id : 1, descripcion: 'Pendiente'},
               {id : 2, descripcion: 'Validación'},
               {id : 3, descripcion: 'Iniciado'},
               {id : 4, descripcion: 'Producción'},
               {id : 5, descripcion: 'Finalizado'}
            ],
            Progresos:[
                {id: 1, descripcion: 'No Iniciada'},
                {id: 2, descripcion: 'En curso'},
                {id: 3, descripcion: 'Completada'}
            ],
            Prioridades:[
                {id: 1, descripcion: 'Baja'},
                {id: 2, descripcion: 'Media'},
                {id: 3, descripcion: 'Alta'},
                {id: 4, descripcion: 'Urgente'}
            ],
            Titulo: '',
            Encargado: '',
            Deposito: '',
            Progreso: '',
            Prioridad: '',
            FechaInicio: '',
            FechaVencimiento: '',
            Notas: '',
            ListaComprobacion:[],
            FilasTabla: []
        }
    },
    methods : {
        GuardarTarea(){
            this.FilasTabla.push(
                {
                title : this.Titulo,
                manager : this.Encargado,
                priority : this.Prioridad,
                finaldate : this.FechaVencimiento,
                notes : this.Notas
                }
            );
            this.$emit('filas', this.FilasTabla);
        }
    }
}
</script>