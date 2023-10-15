<script setup lang="ts">
import G6 from '@antv/g6'
import {onMounted, ref} from "vue";

const containerRef = ref();
const graph = ref();
onMounted(async () => {
  graph.value = new G6.Graph({
    container: containerRef.value,
    width: 1920,
    height: 1080,
    fitView: true,
    fitViewPadding: [20, 40, 50, 20],
  })
  const res = await fetch('https://gw.alipayobjects.com/os/basement_prod/6cae02ab-4c29-44b2-b1fd-4005688febcb.json')
  const remoteData = await res.json()
  graph.value.data(remoteData)
  graph.value.render()
})


</script>

<template>
  <div ref="containerRef"></div>
</template>

<style scoped>

</style>
