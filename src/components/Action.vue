<template>
  <div>
    <button class="" @click="showModal = true">Agregar movimiento</button>
    <teleport to="#app">
      <Modal v-show="showModal" @close="showModal = false">
        <form @submit.prevent="submit">
          <div class="field">
            <label for="label">Title</label>
            <input type="text" id="label" v-model="title" />
          </div>
          <div class="field">
            <label for="amount">Monto</label>
            <input type="number" id="amount" v-model="amount" />
          </div>
          <div class="field">
            <label for="description">Descripción</label>
            <textarea
              rows="4"
              type="text"
              id="description"
              v-model="description"
            />
          </div>
          <div class="field">
            <p>Tipo de movimiento</p>
            <label class="radio-label">
              <input type="radio" value="ingreso" v-model="typeOfMovement" />
              <span>Ingreso</span>
            </label>
            <label class="radio-label">
              <input type="radio" value="gasto" v-model="typeOfMovement" />
              <span>Gasto</span>
            </label>
          </div>
          <div class="submit">
            <button>Agregar</button>
          </div>
        </form>
      </Modal>
    </teleport>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Modal from "./Modal.vue";

const showModal = ref(false);

const title = ref("");
const amount = ref(0);
const description = ref("");
const typeOfMovement = ref("ingreso");
console.log(typeOfMovement.value);

const emit = defineEmits(["create"]);

const submit = () => {
  showModal.value = !showModal.value;
  const newAmount =
    typeOfMovement.value === "ingreso" ? amount.value : -amount.value;
  console.log(newAmount);
  emit("create", {
    title: title.value,
    description: description.value,
    amount: newAmount,
  });
  title.value = "";
  amount.value = 0;
  description.value = "";
};
</script>

<style scoped>
button {
  color: white;
  font-size: 1.25rem;
  background-color: var(--brand-blue);
  border: none;
  width: 100%;
  padding: 24px 60px;
  border-radius: 60px;
  box-sizing: border-box;
}

form {
  font-size: 1.24rem;
  width: 100%;
  background: #fff;
}

form .action {
  padding: 0 24px;
}

.field {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  padding: 16px 24px;
  color: var(--brand-blue);
}

label {
  margin-bottom: 8px;
}

input,
textarea {
  font-size: 1.24rem;
  border: 2px solid var(--brand-blue);
  border-radius: 8px;
  padding: 8px;
}

input[type="number"] {
  text-align: right;
}

.radio-label {
  display: flex;
  align-items: center;
  margin-top: 8px;
}

.radio-label span {
  margin-top: 4px;
  margin-left: 8px;
}

input[type="radio"] {
  appearance: none;
  width: 1.24rem;
  height: 1.24rem;
  color: var(--brand-blue);
  border: 2px solid var(--brand-blue);
  border-radius: 50%;
}

input[type="radio"]:checked {
  background-color: var(--brand-blue);
}
</style>
