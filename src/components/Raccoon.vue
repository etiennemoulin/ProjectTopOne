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
    <div class="Progress">
      <label for="file">Friendship progress : </label>
      <progress id="file" max="100" :value="counter"> {{ counter }} % </progress>
    </div>
      <img alt="Raccoon cute" :src="raccoon_emotion" usemap=#cuteRaccoon>
      <map name="cuteRaccoon" id="cuteRaccoon">
          <area shape="rect" alt="" title="Left ear" coords="155,68,225,159" href="#Raccoon" @click="change_raccoon_emotion('angry', -10)"/>
          <area shape="rect" alt="" title="Right ear" coords="340,38,417,102" href="#Raccoon" @click="change_raccoon_emotion('angry', -10)" />
          <area shape="rect" alt="" title="Nose" coords="358,199,399,230" href="#Raccoon" @click="change_raccoon_emotion('sad', -20)" />
          <area shape="rect" alt="" title="Left eye" coords="283,151,311,174" href="#Raccoon" @click="change_raccoon_emotion('sad', -20)" />
          <area shape="rect" alt="" title="Right eye" coords="366,141,385,165" href="#Raccoon" @click="change_raccoon_emotion('sad', -20)"/>
          <area shape="rect" alt="" title="Forehead" coords="236,80,360,142" href="#Raccoon" @click="change_raccoon_emotion('love', 20)" />
          <area shape="rect" alt="" title="Left paw" coords="25,431,124,453" href="#Raccoon" @click="change_raccoon_emotion('vangry', -20)" />
          <area shape="rect" alt="" title="Right paw" coords="411,447,492,477" href="#Raccoon" @click="change_raccoon_emotion('vangry', -20)" />
          <area shape="rect" alt="" title="Belly" coords="206,277,376,444" href="#Raccoon" @click="change_raccoon_emotion('love', 20)" />
          <area shape="rect" alt="" title="Shoulder" coords="413,302,486,392" href="#Raccoon" @click="change_raccoon_emotion('shy', 20)" />
      </map>
    <div class="Nourriture">
      <input type="image" id="image" alt="Pizza" src="../assets/pizza.png" class="Food">
      <input type="image" id="image" alt="Egg" src="../assets/pizza.png" class="Food">
      <input type="image" id="image" alt="Cream" src="../assets/pizza.png" class="Food">
      <input type="image" id="image" alt="Strawberry" src="../assets/pizza.png" class="Food">
    </div>
      <victorymodale :revele="reveleVictory" :toggleModale="toggleVictoryModale"></victorymodale>
      <loosemodale :revele="reveleLoose" :toggleModale="toggleLooseModale"></loosemodale>
    <p>ICI BARRE DE NOURRITURE, METTRE LES PHOTOS EN PETIT</p>
  </div>
</template>

<script>
//change_raccoon_emotion('angry', -20)
import neutral_raccoon from "../../img/raccoon.png"
import angry_raccoon from "../../img/angry_raccoon.png"
import in_love_raccoon from "../../img/in_love_raccoon.png"
import sad_raccoon from "../../img/sad_raccoon.png"
import shy_raccoon from "../../img/shy_raccoon.png"
import very_angry_raccoon from "../../img/very_angry_raccoon.png"
import VictoryModale from "./VictoryModale";
import LooseModale from "./LooseModale";
//import sad_raccoon from "" //ATTENTION SI LE CHEMIN EST VIDE L'APPLI PLANTE

export default {
  name: 'Raccoon', //Nom du composant
  props: { //Variables transmisent par le parent du composant
    msg: String
  },
  data() { //Donnees du composant, modifiables
    return {
      counter: 20,
      raccoon_emotion : neutral_raccoon,
      reveleVictory: false,
      reveleLoose: false
    }
  },
  components: {
    victorymodale: VictoryModale,
    loosemodale: LooseModale
  },
  methods : { //Fonctions utilisées dans le composant
    change_raccoon_emotion (emotion, n) { //Fonction qui change l'émotion du Raccoon, incrémente le compteur et gère la victoire
      switch(emotion) {
        case ("shy"):
          this.raccoon_emotion = shy_raccoon
          break
        case ("angry") :
          this.raccoon_emotion = angry_raccoon
          break
        case ("love") :
          this.raccoon_emotion = in_love_raccoon
          break
        case ("sad") :
          this.raccoon_emotion = sad_raccoon
          break
        case ("vangry") :
          this.raccoon_emotion = very_angry_raccoon
          break
        default :
          this.raccoon_emotion = neutral_raccoon
      }
      this.counter = this.counter+n
      if (this.counter >= 100) {
        this.toggleVictoryModale()()
      } else if (this.counter <= 0) {
        this.toggleLooseModale()
      }
    },
    toggleVictoryModale() {
      this.reveleVictory = !this.reveleVictory;
    },
    toggleLooseModale() {
      this.reveleLoose = !this.reveleLoose;
    } 
  }
}
</script>

<style scoped>

@media (max-width: 650px) {
 .Raccoon {
    position: top;
    display: flex;
    flex-direction: column;
    align-items: center;
    
  }

  .Progress{
    display: flex;
    flex-direction: column;
    padding: 5em;
  }

  .Nourriture {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    border: 2px solid rgb(111,41,97);
    background-color: aquamarine;
    border-radius: 5px;
    
    
  }

  .Food {
    padding: 5em;
    max-width: 10em;
    
  }

}
@media (min-width: 650px) {
  .Raccoon {
    display: flex;
    flex-direction: column;
    align-items: center;
    
  }

  .Nourriture {
    display: flex;
    border: 2px solid rgb(111,41,97);
    background-color: aquamarine;
    border-radius: 20px;
    
  }

  .Food {
    padding: 5em;
  }

}


</style>