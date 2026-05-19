<script setup>
import Predictor from '@/assets/Predict.png'
import Bolt from '@/assets/svg/Bolt.vue'
import { usePredictionStore } from '@/stores/prediction.js'
import { ErrorCodes } from 'vue'

const predictionStore = usePredictionStore()

const handlePredict = async () => {
  try {
    await predictionStore.predict()
  } catch (error) {
    throw error
    console.log(error)
  }
}
</script>
<template>
  <div class="flex flex-col h-screen items-center justify-center max-w-3xl m-auto">
    <img :src="Predictor" alt="" class="rounded-lg max-w-200" />
    <h2 class="text-3xl font-bold font-headline my-5">Todavía no hay actividades</h2>
    <p class="font-body text-center">
      El entorno de simulación requiere datos históricos para calibrar sus algoritmos de
      rendimiento. Nuestro modelo utiliza análisis de regresión multivariable e inferencia bayesiana
      para proyectar tus métricas.
    </p>
    <p class="font-body text-neutral text-xs text-center my-5">
      ¿Cómo activarlo? <br />
      Sube un archivo CSV válido con tus entrenamientos. <br />
      Define tus zonas de intensidad y umbrales clínicos.
    </p>
    <RouterLink to="/dashboard/upload">
      <Button
        class="flex bg-primary-too-dark p-4 rounded-lg text-white font-label capitalize tracking-wide gap-2 hover:bg-primary-dark mt-5 cursor-pointer"
      >
        <Bolt />
        <p>Añadir tus primeras actividades</p>
      </Button>
    </RouterLink>
  </div>
</template>
