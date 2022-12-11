<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'app-' + block.type"
        :value="block.value"
      >
      </component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>
<script>
import AppTitle from "./AppTitle.vue";
import AppAvatar from "./AppAvatar.vue";
import AppSubtitle from "./AppSubtitle.vue";
import AppText from "./AppText.vue";
export default {
  props: ["blocks"],
  components: { AppTitle, AppAvatar, AppSubtitle, AppText },
};
</script>
