<template>
  <div class="difficulty-screen">
    <div class="screen-header">Como está seu tempo?</div>
    <div class="screen-sub-header">
      Quanto mais longa sua sessão de estudos, mais rápido irá aprender!
    </div>
    <DifficultySelector
      :items="[
        {
          header: 'Curtinho',
          desc: '15 a 30 minutos de estudo',
          key: 'curtinho',
          modalHeader: 'Curtinho',
          modalDesc: `Sem problemas, caso tenha poucas cartas ou esteja um pouco sem tempo esse modo de estudo é o ideal.
             <br/> <br/>
             Importante se lembrar que sempre que tiver o modo <b>ideal</b> disponível, deve estudar por ele ok?`
        },
        {
          header: 'Quase lá',
          desc: '30 a 45 minutos de estudo',
          key: 'quase-la',
          modalHeader: 'Quase lá...',
          modalDesc: `Estamos no caminho certo! 
             <br/> <br/>
             Caso não tenha cartas para o modo ideal, tudo bem estudar por esse.`
        },
        {
          header: 'Ideal',
          desc: '45 minutos a 1 hora de estudo',
          key: 'ideal',
          modalHeader: 'Ideal!',
          modalDesc: `Perfeito! Esse modo garante o tempo de prática necessária para atingir seus objetivos ao longo prazo. Pode ser que em alguns dias não tenha cartas suficientes para estudar, mas sempre que disponível, procure utilizer esse modo!`
        },
        {
          header: 'Hardcore',
          desc: 'Mais de uma hora de estudo',
          key: 'hardcore',
          modalHeader: 'Hardcore!',
          modalDesc: `Para quem quiser se desafiar. Nesse modo não existe um limite de tempo. 
            <br/> <br/>
            Iremos mostrar cartas até o deck acabar. Uma verdadeira maratona de estudos!`
        }
      ]"
    />
  </div>
</template>

<script>
import DifficultySelector from './DifficultySelector'

export default {
  name: 'DifficultyScreen',
  components: { DifficultySelector },
  data: () => {return {}},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Fira+Sans:300,400,600|Roboto:400,700&display=swap');

/* mobile/tablet/laptop/desktop */
.difficulty-screen {
  background: #f0f0f0;
}
.stopwatch {
  transition: transform 0.16s linear;
  opacity: 0.7;
}
.screen-header {
  font-family: 'Roboto';
  font-weight: 700;
  font-size: 30px;
  color: #000000;
}
.screen-sub-header {
  font-family: 'Fira Sans';
  word-spacing: 0.5px;
  opacity: 0.45;
  margin-bottom: 0.7em;
}

/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .difficulty-screen {
    padding-top: 30px;
  }
  .stopwatch {
    margin-top: 100% !important;
  }
  .stopwatch-bounce {
    transform: translateY(-2px);
    opacity: 1;
  }
  .screen-header {
    text-align: left;
    margin-left: 2rem;
    font-size: 30pt !important;
    line-height: 1;
  }
  .modal-dialog {
    bottom: 0;
    position: absolute !important;
  }
  .stopwatch-screen > svg {
    display: none !important;
    visibility: hidden !important;
    opacity: 0 !important;
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
  .stopwatch-mobile > svg {
    display: none !important;
    visibility: hidden !important;
    opacity: 0 !important;
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
  }
}
</style>
