<template>
  <div>
    <button @click="randomStart()" class="btn btn-danger btn-lg mb-2"><svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-power" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" d="M5.578 4.437a5 5 0 1 0 4.922.044l.5-.866a6 6 0 1 1-5.908-.053l.486.875z"/>
  <path fill-rule="evenodd" d="M7.5 8V1h1v7h-1z"/>
</svg></button>
    <div class="row">
      <div class="col">
        <button @click="randomDamage(3,10)" class="btn btn-primary mb-4">Attack</button> 
        <button @click="randomDamageSP(10,20)" class="btn btn-warning mb-4">SP Attack</button> 
      </div>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="col">
          <div class="alert alert-light" role="alert">Hero : {{randomPlayer}} HP : {{hp1}}</div> 
          <img :src="image1" class="img-fluid" />
        </div>
        <div class="col">
          <div class="alert alert-light" role="alert">Hero : {{randomMonster}} HP : {{hp2}}</div> 
          <img :src="image2" class="img-fluid" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomAttack: "",
      randomSpAttack: "",
      image1: "",
      image2: "",
      hp1: "",
      hp2: "",
      win: "./image/win.jpg", 
      lose: "./image/lose.jpg", 
      player: [
        {
          name: "cookie", 
          hp: 101, 
          image: "./image/cookie.png", 
        },
        {
          name: "deku", 
          hp: 300, 
          image: "./image/deku.png", 
        },
        {
          name: "astar", 
          hp: 1000, 
          image: "./image/aster.png", 
        },
        {
          name: "yuki", 
          hp: 250, 
          image: "./image/yuki.jpg", 
        },
      ],
      randomPlayer: "",
      monster: [
        {
          name: "black", 
          hp: 350, 
          image: "./image/black.png", 
        },
        {
          name: "devill", 
          hp: 102, 
          image: "./image/devill.png", 
        },
        {
          name: "allforone", 
          hp: 230, 
          image: "./image/allofrone.png",
           
        },
        {
          name: "giant", 
          hp: 1999, 
          image: "./image/giant.jpg",
        },
      ],
      randomMonster: "",
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[chosenNumber1].name;
      this.hp1 = this.player[chosenNumber1].hp;
      this.image1 = this.player[chosenNumber1].image;

      var chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[chosenNumber2].name;
      this.hp2 = this.monster[chosenNumber2].hp;
      this.image2 = this.monster[chosenNumber2].image;
    },

    randomDamage: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp1 -= this.randomAttack;
      }
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },

    randomDamageSP: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },
  },
};
</script>

<style>
</style>