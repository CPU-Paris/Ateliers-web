<template>
  <div>
    <navbar></navbar>
    <main >

        <p>Vous êtes sur la page de réservation d'hotel. Voici votre panier : </p>

        <section v-if="nbSecondes >= 0" >
            <h1>Vous avez {{nbSecondes}}s pour faire votre achat</h1>
            <p>Vous allez dormir {{nbJours}} jours ! <button @click="nbJours--">- jours</button> <button @click="nbJours++">+ jours</button></p>
            <achats :items="this.items" class="ok"></achats>
        </section>
        <p v-else class="nope">
            Fini tu peux plus choisir.

        </p>

        <p>Prix total : {{prixPanier}}€</p>
        <button @click="nbSecondes += 10">Ajouter 10 secondes dans le timeout</button>
    </main>
  </div>
</template>

<script>
import achats from '../components/achats.vue';
import Navbar from '../components/navbar.vue'
export default {
  components: { achats },

    data() {
        return {
            nbJours: 1,
            nbSecondes: 20,
            items: [
                {name: "Adulte", prix: 40, qte: 0, stock: 3},
                {name: "Enfant", prix: 30, qte: 0, stock: 3},
                {name: "Chien", prix: 10, qte: 0, stock: 1},
            ]
        }
    },
    computed: {
        prixPanier() {
            let prixTot = 0;
            for (let item of this.items) {
                prixTot+= item.prix * item.qte;
            }
            return prixTot * this.nbJours;
        }

    },
    created() {
        setInterval(this.tictac, 1000);
    },
    methods: {
        tictac() {
            this.nbSecondes--;
        }
    }
}
</script>

<style scoped>
main {
    margin: 2em 10%;
    padding: 2em;
}
.ok {
    background: cornsilk;
}
.nope {
    background: coral;
}
.ok, .nope {
    padding: 1em;
}
</style>