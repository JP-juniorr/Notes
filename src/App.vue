<script setup></script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button>+</button>
      </header>
      <div class="cards-container">
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nihil,
            iure impedit fuga obcaecati neque enim commodi est tempore molestias
            voluptatibus blanditiis atque nostrum quis nobis ex aperiam suscipit
            corporis repellat eos animi
          </p>
          <p class="date">2023-10-01 12:00</p>
        </div>
        <div class="card">
          <p class="main-text">
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Nihil,
            iure impedit fuga obcaecati neque enim commodi est tempore molestias
            voluptatibus blanditiis atque nostrum quis nobis ex aperiam suscipit
            corporis repellat eos animi
          </p>
          <p class="date">2023-10-01 12:00</p>
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
button {
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
  color: #fff;
  text-align: right;
}
.cards-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
</style>
