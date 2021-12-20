<template>
  <div class="bloc-modale" v-if="revele">
    <div class="overlay" v-on:click="toggleModale"></div>

    <div class="modale card">
      <div>
        <h2>VICTOIRE, TU AS ADOPTE LE PETIT RACCOON</h2>
        <img alt="Raccoon cute" :src="defineImg()" usemap=#cuteRaccoon width="400" height="400">
      </div>
      <div>
        <button @click="toggleModale()">Rejouer</button>
      </div>
    </div>
  </div>
</template>


<script>
import victory1 from "../../img/victory1.png"
import victory2 from "../../img/victory2.png"

let victoryImg = [victory2, victory1]

export default {
  name: "VictoryModale",
  methods : {
    defineImg() {
      return(victoryImg[Math.floor(Math.random() * 2)])
    }
  },
  props: ["revele", "toggleModale"]
};
</script>


<style scoped>
.bloc-modale {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.overlay {
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}

.modale {
  background: #f1f1f1;
  color: #333;
  padding: 50px;
  position: fixed;
  top: 10%;
}

button {
  display: inline-block;
  background-color: #7b38d8;
  border-radius: 10px;
  border: 4px double #cccccc;
  color: #eeeeee;
  text-align: center;
  font-size: 14px;
  padding: 10px;
  width: 100px;
  transition: all 0.5s;
  cursor: pointer;
  margin: 5px;
}
button span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}
button span:after {
  content: "\00bb";
  position: absolute;
  opacity: 0;
  top: 0;
  right: -20px;
  transition: 0.5s;
}
button:hover {
  background-color: #f7c2f9;
}
button:hover span {
  padding-right: 25px;
}
button:hover span:after {
  opacity: 1;
  right: 0;
}
</style>