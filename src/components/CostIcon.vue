<script setup lang="ts">
import { Cost } from "~/common/interfaces/Cost"

const props = defineProps<{
  cost: Cost
}>()

const iconUrl = computed(() => `url("${getIcon(props.cost.type)}")`)
</script>

<template>
  <div class="icon font_shadow">
    {{ cost.count }}
  </div>
</template>

<style scoped>
.icon {
  background-image: v-bind(iconUrl);
  background-size: 100% 100%;
  width: 100%;
  height: 0;
  padding: 50% 0;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
