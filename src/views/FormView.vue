<template>
  <div>
    <h2>Registrar Idea</h2>
    <form @submit.prevent="guardar">
      <input v-model="idea.titulo" placeholder="Título" required />
      <input v-model="idea.descripcion" placeholder="Descripción" required />
      <input v-model="idea.area" placeholder="Área" required />
      <input v-model="idea.beneficio" placeholder="Beneficio esperado" required />

      <select v-model="idea.esfuerzo">
        <option value="">Esfuerzo estimado</option>
        <option value="bajo">Bajo</option>
        <option value="medio">Medio</option>
        <option value="alto">Alto</option>
      </select>

      <select v-model="idea.impacto">
        <option value="">Impacto estimado</option>
        <option value="bajo">Bajo</option>
        <option value="medio">Medio</option>
        <option value="alto">Alto</option>
      </select>

      <button type="submit">Guardar</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const idea = ref({
  titulo: '', descripcion: '', area: '',
  beneficio: '', esfuerzo: '', impacto: ''
})

function calcularPrioridad(impacto, esfuerzo) {
  if (impacto === 'alto' && esfuerzo === 'bajo') return 'Alta'
  if (impacto === 'alto' && esfuerzo === 'medio') return 'Alta'
  if (impacto === 'alto' && esfuerzo === 'alto') return 'Media'
  if (impacto === 'medio' && esfuerzo === 'bajo') return 'Media'
  if (impacto === 'medio' && esfuerzo === 'medio') return 'Media'
  if (impacto === 'medio' && esfuerzo === 'alto') return 'Baja'
  if (impacto === 'bajo' && esfuerzo === 'bajo') return 'Media'
  if (impacto === 'bajo' && esfuerzo === 'medio') return 'Baja'
  if (impacto === 'bajo' && esfuerzo === 'alto') return 'Baja'
  return 'Media'
}

function guardar() {
  const ideas = JSON.parse(localStorage.getItem('ideas') || '[]')
  ideas.push({ ...idea.value, prioridad: calcularPrioridad(idea.value.impacto, idea.value.esfuerzo) })
  localStorage.setItem('ideas', JSON.stringify(ideas))
  router.push('/')
}
</script>