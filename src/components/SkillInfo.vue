<script setup lang="ts">
import { ISkill } from "~/common/interfaces/ISkill"

defineProps<{
  characterName: string
  index: number
  skill: ISkill
}>()

const isSelected = ref(false)
</script>

<template>
  <div class="skillInfo" @click="isSelected = !isSelected">
    <img :src="getSkill(characterName, index)" />

    <div>
      <p>{{ skill.name }}</p>
      <div class="costs">
        <div v-for="cost in skill.cost">
          <cost-icon :cost="cost" />
        </div>
      </div>
    </div>
  </div>

  <transition name="fade">
    <p class="desc" v-html="skill.desc" v-if="isSelected"></p>
  </transition>
</template>

<style scoped lang="scss">
.skillInfo {
  display: flex;
  border: grey 1.5px solid;
  border-radius: 8px;
  padding: 3%;
  align-items: center;
  margin-bottom: 3%;

  img {
    width: 27%;
    border-radius: 50%;
    border: grey 2px solid;
  }

  > div {
    margin-left: 10px;
    width: 100%;

    > p {
      font-size: 30px;
    }

    .costs {
      display: flex;

      > div {
        width: 25%;
      }
    }
  }
}

.desc {
  border: grey 2px solid;
  border-radius: 8px;
  font-size: 30px;
  padding: 0 3%;
  margin: 0 3%;
  margin-bottom: 3%;
}
</style>
