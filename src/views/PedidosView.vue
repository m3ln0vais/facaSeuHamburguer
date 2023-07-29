<template>
  <div>
    <div class="text-center py-3">
      <h1>Gerenciar pedidos:</h1>
      <Dashboard />
    </div>
  </div>
</template>

<script>
import Dashboard from '../components/Dashboard'

export default {
  name: 'pedidos',
  components: {
    Dashboard
  }
}
</script>