<template>
  <img v-if="img" :src="img" >
  <div class="bg-dark" >
    <div>
      <div class="space1"></div>
      <input 
        v-model="question"
        type="text" 
        placeholder="Hazme una pregunta"
      >
      <p>Recuerda terminar con un signo de interrogación (?)</p>
      <div>
        <h2>{{answer }}</h2>  
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: null,
      answer: null,
      img: null,
    }
  },
  methods: { 
    async getAnswers() {
      this.answer = "Pensando..."
      const {answer, image} = await fetch("https://yesno.wtf/api").then( r => r.json() )
      this.answer = answer
      this.img = image
      
    }
  },
  watch: {
    question (value) {
      if (  !value.includes("?")) return
      
      this.getAnswers()
    }
  }
}
</script>

<style scoped>

    img, .bg-dark {
        height: 100vh;
        left: 0px;
        max-height: 100%;
        max-width: 100%;
        position: fixed;
        top: 0px;
        width: 100vw;
    }

    .bg-dark {
        background-color: rgba(0, 0, 0, 0.4);
    }

    .space1 {
      height: 150px;

    }

    .indecision-container {
        position: relative;
        z-index: 99;
    }
    
    input {
        width: 250px;
        padding: 10px 15px;
        border-radius: 5px;
        border: none;
    }
    input:focus {
        outline: none;
    }

    p {
        color: white;
        font-size: 20px;
        margin-top: 0px;
    }

    h1, h2 {
        color: white;
    }
    
    h2 {
        margin-top: 150px;
    }

</style>