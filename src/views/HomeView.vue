<template>
  <div>
    <h2>Ideas de Innovación</h2>
    <p v-if="ideas.length === 0">No hay ideas registradas.</p>
    <table v-else>
      <thead>
        <tr>
          <th>Título</th>
          <th>Descripción</th>
          <th>Área</th>
          <th>Beneficio</th>
          <th>Impacto</th>
          <th>Esfuerzo</th>
          <th>Prioridad</th>
          <th>Acciones</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(idea, i) in ideas" :key="i">
          <td>{{ idea.titulo }}</td>
          <td>{{ idea.descripcion }}</td>
          <td>{{ idea.area }}</td>
          <td>{{ idea.beneficio }}</td>
          <td style="text-transform: capitalize">{{ idea.impacto }}</td>
          <td style="text-transform: capitalize">{{ idea.esfuerzo }}</td>
          <td :style="{ color: idea.prioridad === 'Alta' ? 'green' : idea.prioridad === 'Baja' ? 'red' : 'orange' }">
            {{ idea.prioridad }}
          </td>
          <td>
            <button @click="eliminar(i)" style="background:red; padding: 6px 10px;">🗑️</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const ideas = ref(JSON.parse(localStorage.getItem('ideas') || '[]'))

function eliminar(index) {
  ideas.value.splice(index, 1)
  localStorage.setItem('ideas', JSON.stringify(ideas.value))
}
</script>