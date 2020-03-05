<template>
  <div class="difficulty-screen">
    <div class="screen-header">Como está seu tempo?</div>
    <div class="screen-sub-header">
      Quanto mais longa sua sessão de estudos, mais rápido irá aprender!
    </div>
    <DifficultySelector :items="items" />
  </div>
</template>

<script>
import DifficultySelector from "./DifficultySelector"

export default {
  name: "DifficultyScreen",
  components: { DifficultySelector },
  data: () => {
    return {
      items: [
        {
          header: "Curtinho",
          desc: "15 a 30 minutos de estudo",
          key: "curtinho",
          modal: {
            header: "Curtinho",
            desc: `Sem problemas, caso tenha poucas cartas ou esteja um pouco sem tempo esse modo de estudo é o ideal.
             <br/> <br/>
             Importante se lembrar que sempre que tiver o modo <b> ideal </b> disponível, deve estudar por ele ok?`
          },
          isDisabled: false
        },
        {
          header: "Quase lá",
          desc: "30 a 45 minutos de estudo",
          key: "quase-la",
          modal: {
            header: "Quase lá...",
            desc: `Estamos no caminho certo! 
             <br/> <br/>
             Caso não tenha cartas para o modo ideal, tudo bem estudar por esse.`
          },
          isDisabled: false
        },
        {
          header: "Ideal",
          desc: "45' a 1 hora de estudo",
          key: "ideal",
          modal: {
            header: "Ideal!",
            desc: `Perfeito! Esse modo garante o tempo de prática necessária para atingir seus objetivos ao longo prazo. Pode ser que em alguns dias não tenha cartas suficientes para estudar, mas sempre que disponível, procure utilizer esse modo!`
          },
          isDisabled: false
        },
        {
          header: "Hardcore",
          desc: "Mais de 1 hora de estudo",
          key: "hardcore",
          modal: {
            header: "Hardcore!",
            desc: `Para quem quiser se desafiar. Nesse modo não existe um limite de tempo. 
            <br/> <br/>
            Iremos mostrar cartas até o deck acabar. Uma verdadeira maratona de estudos!`
          },
          isDisabled: true
        }
      ]
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Fira+Sans:300,400,600|Roboto:100,300,400,700&display=swap");
.difficulty-screen {
  background: #f0f0f0;
}
/* iphone 5 and other 320px */
@media (min-width: 320px) and (max-width: 380px) {
  .desc span:nth-child(2) {
    display: block;
  }
  .screen-header {
    margin-top: 2rem;

  }
}
/* mobile/tablet/laptop/desktop */
.desc-break {
  margin-top: 0.8em;
}

.stopwatch {
  transition: transform 0.16s linear;
  opacity: 0.8;
}
.stopwatch-screen {
  margin-bottom: 0.52em;
}
.screen-header {
  font-family: "Roboto";
  font-weight: 700;
  font-size: 30px;
  color: #000000;
}
.screen-sub-header {
  font-family: "Fira Sans";
  word-spacing: 0.5px;
  opacity: 0.45;
  line-height: 1.4;
}
/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  /* descriptions that need a line break on mobile have a span wrapping each desc string */
  /* in parent element because vue scoped styles do not apply to spa v-html attribtues */
  .desc {
    text-align: left;
  }

  .difficulty-screen {
    padding-top: 5px;
  }
  .stopwatch {
    height: 100%;
  }
  .screen-header {
    text-align: left;
    margin-left: 2rem;
    font-size: 26pt;
    line-height: 1;
    margin-top: 1rem;
  }
  .screen-sub-header {
    width: 80%;
    margin-bottom: 0.7em;
  }
  .modal-dialog {
    bottom: 0;
    position: absolute !important;
  }

  .stopwatch-screen > img {
    display: none !important;
    visibility: hidden !important;
    opacity: 0 !important;
  }
  .screen-sub-header {
    margin-top: 1em;
    text-align: left;
    font-size: 14px;
    margin-left: 2rem;
  }
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {
  .difficulty-screen {
    padding-top: 60px;
  }
  .stopwatch-bounce {
    transform: translateY(-6px);
    opacity: 1;
  }

  .stopwatch-mobile > img {
    display: none !important;
    visibility: hidden !important;
    opacity: 0 !important;
  }
  .screen-header {
    line-height: 1.2;
  }
  .screen-sub-header {
    text-align: center;
    font-size: 12px;
    margin-bottom: 1.7em;
  }
}
</style>
