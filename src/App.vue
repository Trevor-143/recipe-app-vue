<template>
  <header>
    <div class="top">
      <img src="./assets/meal.png" alt="app logo">
      <h3>Delish Delight</h3>
    </div>
    
  </header>
  <router-view/>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500;600;700;800;900&display=swap');

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'poppins', sans-serif;
  }
  .top {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    margin-top: 20px;
  }
  .top img {
    width: 50px;
    margin: 10px;
  }
  .top h3 {
    font-size: 20px;
    color: #464646;
  }
  .form {
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: center;
  }
  form {
    display: flex;
    padding: 7px;
    border-radius: 99px;
    align-items: center;
    justify-content: space-between;
    max-width: 600px;
    width: 100%;
    margin: 15px;
    background: #e4e3ff;
  }
  form input {
    width: 80%;
    border: none;
    background: none;
    padding-left: 15px;
  }
  form input:focus {
    outline: none;
    background: none;
  }
  form button {
    padding: 10px;
    border-radius: 99px;
    border: none;
    background: #262455;
    color: #fff;
  }
</style>
