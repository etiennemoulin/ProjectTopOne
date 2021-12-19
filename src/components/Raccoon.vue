<!--
PETITE AIDE POUR COMPRENDRE VUE.JS

Appeler un élément de Data dans une balise html : 
<p> {{ma_variable}} </p>

Appeler un élément de Data dans un argument d'une balise :
<progress id="file" max="100" :value="ma_variable">

PROPOSITION DE PRESENTATION :

BARRE DU PROGRESSION EN HAUT DE L'ECRAN
RACCOON EN DESSOUS
BARRE AVEC PROPOSITION DE NOURRITURE EN DESSOUS DU RACCON
Gestion des points d'alimentation au clic, si trop chiant de faire un drag and drop
-->
<template>
  <div class="Raccoon">
      <label for="file">Friendship progress : </label>
      <progress id="file" max="100" :value="counter"> {{ counter }} % </progress>
      <img alt="Raccoon cute" :src="raccoon_emotion" usemap=#cuteRaccoon>
      <map name="cuteRaccoon" id="cuteRaccoon">
          <area shape="rect" alt="" title="Left ear" coords="155,68,225,159" href="#Raccoon" @click="change_raccoon_emotion('h', -20)"/>
          <area shape="rect" alt="" title="Right ear" coords="340,38,417,102" href="#Raccoon" @click="change_raccoon_emotion('h', -20)" />
          <area shape="rect" alt="" title="Nose" coords="358,199,399,230" href="#Raccoon" @click="change_raccoon_emotion('h', -20)" />
          <area shape="rect" alt="" title="Left eye" coords="283,151,311,174" href="#Raccoon" @click="change_raccoon_emotion('h', -20)" />
          <area shape="rect" alt="" title="Right eye" coords="366,141,385,165" href="#Raccoon" @click="change_raccoon_emotion('h', -20)"/>
          <area shape="rect" alt="" title="Forehead" coords="236,80,360,142" href="#Raccoon" @click="change_raccoon_emotion('h', 20)" />
          <area shape="rect" alt="" title="Left paw" coords="25,431,124,453" href="#Raccoon" @click="change_raccoon_emotion('h', -20)" />
          <area shape="rect" alt="" title="Right paw" coords="411,447,492,477" href="#Raccoon" @click="change_raccoon_emotion('h', -20)" />
          <area shape="rect" alt="" title="Belly" coords="206,277,376,444" href="#Raccoon" @click="change_raccoon_emotion('h', 20)" />
          <area shape="rect" alt="" title="Shoulder" coords="413,302,486,392" href="#Raccoon" @click="change_raccoon_emotion('h', 20)" />
      </map>
    <p>ICI BARRE DE NOURRITURE, METTRE LES PHOTOS EN PETIT</p>
  </div>
</template>

<script>
//change_raccoon_emotion('angry', -20)
import neutral_raccoon from "../../img/raccoon.png"
import happy_raccoon from "../../img/raccooncute.png"
import angry_raccoon from "../../img/angryraccoon.jpg"
//import sad_raccoon from "" //ATTENTION SI LE CHEMIN EST VIDE L'APPLI PLANTE

export default {
  name: 'Raccoon', //Nom du composant
  props: { //Variables transmisent par le parent du composant
    msg: String
  },
  data() { //Donnees du composant, modifiables
    return {
      counter: 20,
      raccoon_emotion : neutral_raccoon
    }
  },
  methods : { //Fonctions utilisées dans le composant
    change_raccoon_emotion (emotion, n) { //Fonction qui change l'émotion du Raccoon, incrémente le compteur et gère la victoire
      switch(emotion) {
        case ("happy"):
          this.raccoon_emotion = happy_raccoon
          break
        case ("angry") :
          this.raccoon_emotion = angry_raccoon
          break
       // case ("sad") :
       //   this.raccoon_emotion = sad_raccoon
        //  break
        default :
          this.raccoon_emotion = neutral_raccoon
      }
      this.counter = this.counter+n
      if (this.counter >= 100) {
        this.win()
      } else if (this.counter <= 0) {
        this.loose()
      }
    },
    win() {
      alert('You win')
    },
    loose() {
      alert('You loose')
    } 
  }
}
</script>
