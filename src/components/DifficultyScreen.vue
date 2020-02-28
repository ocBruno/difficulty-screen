<template>
  <div class="difficulty-screen">
    <div class="header">Como está seu tempo?</div>
    <div class="sub-header">
      Quanto mais longa sua sessão de estudos, mais rápido irá aprender!
    </div>
    <DifficultySelector
      :items="[
        {
          header: 'Curtinho',
          desc: '15 a 30 minutos de estudo',
          key: 'curtinho',
          modalHeader: 'Curtinho',
          modalDesc:
            `Sem problemas, caso tenha poucas cartas ou esteja um pouco sem tempo esse modo de estudo é o ideal.
             <br/> <br/>
             Importante se lembrar que sempre que tiver o modo <b>ideal</b> disponível, deve estudar por ele ok?`
        },
        {
          header: 'Quase lá',
          desc: '30 a 45 minutos de estudo',
          key: 'quase-la',
          modalHeader: 'Quase lá...',
          modalDesc:
            `Estamos no caminho certo! 
             <br/> <br/>
             Caso não tenha cartas para o modo ideal, tudo bem estudar por esse.`
        },
        {
          header: 'Ideal',
          desc: '45 minutos a 1 hora de estudo',
          key: 'ideal',
          modalHeader: 'Ideal!',
          modalDesc:
            `Perfeito! Esse modo garante o tempo de prática necessária para atingir seus objetivos ao longo prazo. Pode ser que em alguns dias não tenha cartas suficientes para estudar, mas sempre que disponível, procure utilizer esse modo!`
        },
        {
          header: 'Hardcore',
          desc: 'Mais de uma hora de estudo',
          key: 'hardcore',
          modalHeader: 'Hardcore!',
          modalDesc:
            `Para quem quiser se desafiar. Nesse modo não existe um limite de tempo. 
            <br/> <br/>
            Iremos mostrar cartas até o deck acabar. Uma verdadeira maratona de estudos!`
        }
      ]"
    />
  </div>
</template>

<script>
import DifficultySelector from "./DifficultySelector"

export default {
  name: "DifficultyScreen",
  components: { DifficultySelector }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Fira+Sans:300,400&display=swap");
@import url("https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap");

.difficulty-screen {
  background: #f0f0f0;
}
.header {
  font-family: "Roboto";
  font-weight: 700;
  font-size: 30px;
  line-height: 1.2;
}
.sub-header {
  font-family: "Fira Sans";
  font-size: 12px;
  word-spacing: 0.5px;
  opacity: 0.45;

}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
