<script setup>
import { ref } from "vue";
const overlay = ref(false);
const overlayModel = () => {
  overlay.value = true;
};
const overlayFalse = () => {
  overlay.value = false;
};

const newNote = ref("");
const cards = ref([]);

const getRandomColor = () => {
  return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
};

const addNote = () => {
  if (newNote.value.trim() === "") {
    alert("Please enter a note.");
    return;
  }
  if (newNote.value.length > 100) {
    alert("Note is too long. Please limit to 100 characters.");
    return;
  }
  if (cards.value.length >= 10) {
    alert("You can only have a maximum of 10 notes.");
    return;
  }
  if (cards.value.some((card) => card.text === newNote.value)) {
    alert("This note already exists.");
    return;
  }
  if (newNote.value.length < 5) {
    alert("Note is too short. Please enter at least 5 characters.");
    return;
  }
  if (newNote.value.length > 100) {
    alert("Note is too long. Please limit to 100 characters.");
    return;
  }
  const date = new Date();

  const formattedDate = `${date.getDate()}/${
    date.getMonth() + 1
  }/${date.getFullYear()}`;

  cards.value.push({
    id: Math.floor(Math.random() * 1000),
    text: newNote.value,
    date: formattedDate,
    color: getRandomColor(),
  });

  newNote.value = "";
  overlay.value = false;
};
</script>

<template>
  <main>
    <div v-if="overlay" class="overlay">
      <div class="model">
        <textarea
          v-model="newNote"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <div>
          <button @click="addNote">Add Note</button>
          <button @click="overlayFalse" class="close">X</button>
        </div>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="overlayModel">+</button>
      </header>
      <div class="cards-container">
        <div v-for="card in cards" key="card.id">
          <div class="card" :style="{ background: card.color }">
            <p class="main-text">{{ card.text }}</p>
            <p class="date">{{ card.date }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 1000px;
  padding: 10px;
  margin: 0 auto;
}
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
}
h1 {
  font-size: 75px;
  font-weight: bold;
  margin-bottom: 25px;
  color: #333;
}
header button {
  background-color: rgb(21, 20, 20);
  border: none;
  padding: 10px;
  font-size: 20px;
  height: 50px;
  width: 50px;
  cursor: pointer;
  border-radius: 100%;
  color: white;
  font-size: 20px;
}
.card {
  width: 250px;
  height: 250px;
  background: #cb9a9a;
  padding: 10px;
  border-radius: 15px;
  font-size: 14px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
}
.date {
  font-size: 12px;
  color: #252323;
  text-align: right;
}
.cards-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.77);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}
.model {
  width: 750px;
  padding: 30px;
  background-color: #fff;
  border-radius: 10px;
  position: relative;
  display: flex;
  flex-direction: column;
}
.model button {
  background-color: rgb(21, 20, 20);
  font-size: 18px;
  height: 100%;
  width: 20%;
  cursor: pointer;
  color: white;
  outline: none;
  margin-top: 10px;
  padding: 10px;
  border-radius: 6px;
  border: 1px solid rgb(21, 20, 20);
  margin-right: 20px;
}
.close {
  background: #cb9a9a !important;
  border: 1px solid #cb9a9a !important;
  width: 50px !important;
  height: 100% !important;
}
</style>
