<template>
  <div class="p-4">
    <h1 class="text-6xl font-semibold mb-4">Todo App</h1>
    <p class="text-2xl mb-2">Skriv Todo ting i tekstboksen under</p>
    <input
      type="text"
      class="p-5 border border-[#BFBFBF] rounded-md hover:border-[#242424] w-full h-full text-xl mb-2"
      v-model="currentTekst"
    />
    <br />
    <button
      class="p-5 border border-[#BFBFBF] rounded-md hover:border-[#242424] text-2xl"
      @click="leggTilTodo"
    >
      Legg til
    </button>
    <div v-for="(items, index) in todoListe" :key="index">
      <li
        class="hover:line-through cursor-pointer p-5 border border-[#BFBFBF] rounded-md hover:border-[#242424] w-full h-full my-2"
        @click="removeTodo(index)"
      >
        {{ todoListe[index] }}
      </li>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      currentTekst: "",
      todoListe: [],
    };
  },
  methods: {
    leggTilTodo() {
      if (this.currentTekst != "") {
        this.todoListe.push(this.currentTekst);
        console.log(this.todoListe);
        this.currentTekst = "";
      }
    },
    removeTodo(id: number) {
      this.$delete(this.todoListe, id);
    },
  },
};
</script>
