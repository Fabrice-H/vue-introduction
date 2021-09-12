<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p class="abonne" v-if="abonnes == 0">Aucun abonnés pour le moment 😥</p>
    <p class="abonne" v-else-if="abonnes == 1">Une personne s'est abonnée, c'est un bon début ! 💪</p>
    <p class="abonne" v-else>{{abonnes}} personnes se sont abonnées 🔥</p>
    <button class="comment-btn" @click="subscribe()">S'abonner</button>

    <div class="comment" v-for="(comment, id) in comments" v-bind:key="id">
      <hr>
      <h3> {{comment.nom}} </h3>
      <p> {{comment.commentaire}} </p>
      <div v-if="comment.note > 1">
        <span v-for="i in comment.note" v-bind:key="i">❤️</span>
      </div>
      <span v-else>💩</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      abonnes: 0,
      comments: [
        {
        nom: "Jacques",
        commentaire: "C'est de la bombe !",
        note: 3
      },
      {
        nom: "Marie",
        commentaire: "J'adore ce que tu fais continue.",
        note: 5
      },
      {
        nom: "Inconnu",
        commentaire: "C'est du caca",
        note: 1
      }
      ]
    }
  },
  methods: {
    subscribe() {
      this.abonnes += 1
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  p {
    font-size: 1rem;
  }
  p.abonne {
    font-size: 2rem;
  }
  a {
    color: #42b983;
  }
  button.comment-btn {
    background-color: rgb(145, 14, 14);
    color: #fff;
    font-size: 1.2rem;
    outline: none;
    border: none;
    padding: 6px 12px;
    cursor: pointer;
  }
</style>
