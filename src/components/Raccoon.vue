<!--
PETITE AIDE POUR COMPRENDRE VUE.JS

Appeler un élément de Data dans une balise html : 
<p> {{ma_variable}} </p>

Appeler un élément de Data dans un argument d'une balise :
<progress id="file" max="100" :value="ma_variable">

-->
<template>
  <div class="Raccoon">
    <h1>{{raccoon_emotion}}</h1>
      <label for="file">Friendship progress : </label>
      <progress id="file" max="100" :value="counter"> {{ counter }} % </progress>
      <img alt="Raccoon cute" src="../../img/raccoon.png" usemap=#cuteRaccoon>
      <map name="cuteRaccoon" id="cuteRaccoon">
          <area shape="rect" alt="" title="Left ear" coords="155,68,225,159" href="#Raccoon" @click="increment(20)"/>
          <area shape="rect" alt="" title="Right ear" coords="340,38,417,102" href="#Raccoon" @click="increment(-20)" />
          <area shape="rect" alt="" title="Nose" coords="358,199,399,230" href="#Raccoon" @click="increment(20)" />
          <area shape="rect" alt="" title="Left eye" coords="283,151,311,174" href="#Raccoon" @click="increment(20)" />
          <area shape="rect" alt="" title="Right eye" coords="366,141,385,165" href="#Raccoon" @click="increment(20)"/>
          <area shape="rect" alt="" title="Forehead" coords="236,80,360,142" href="#Raccoon" @click="increment(20)" />
          <area shape="rect" alt="" title="Left paw" coords="25,431,124,453" href="#Raccoon" @click="increment(20)" />
          <area shape="rect" alt="" title="Right paw" coords="411,447,492,477" href="#Raccoon" @click="increment(20)" />
          <area shape="rect" alt="" title="Belly" coords="206,277,376,444" href="#Raccoon" @click="increment(20)" />
          <area shape="rect" alt="" title="Shoulder" coords="413,302,486,392" href="#Raccoon" @click="increment(20)" />
      </map>
  </div>
</template>

<script>
export default {
  name: 'Raccoon', //Nom du composant
  props: { //Variables transmisent par le parent du composant
    msg: String
  },
  data() { //Donnees du composant, modifiables
    return {
      counter: 20,
      raccoon_emotion : '"../../img/raccoon.png"'
    }
  },
  methods : { //Fonctions utilisées dans le composant
    increment (n) {
      this.counter = this.counter+n
    }
  }
}
</script>
