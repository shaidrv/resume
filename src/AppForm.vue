<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="blockType">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="value" id="value" rows="3"></textarea>
    </div>

    <button class="btn primary" :disabled="!isValid">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: ["addBlock"],
  data() {
    return {
      blockType: "title",
      value: "",
    };
  },
  methods: {
    submit() {
      this.$emit("addBlock", {
        value: this.value,
        type: this.blockType,
        id: Date.now(),
      });
      this.value = "";
      this.blockType = "title";
    },
  },
  computed: {
    isValid() {
      return this.value.length > 3;
    },
  },
};
</script>

<style></style>
