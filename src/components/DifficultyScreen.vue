<template>
  <div class="hello">
    <div>
      Como está seu tempo?
    </div>
    <div>
      Quanto mais longa sua sessão de estudos, mais rápido irá aprender!
    </div>
    <DifficultySelector
      :items="[
        { header: 'Curtinho', desc: '15 a 30 minutos de estudo' },
        { header: 'Quase lá', desc: '30 a 45 minutos de estudo' },
        { header: 'Ideal', desc: '45 minutos a 1 hora de estudo' },
        { header: 'Hardcore', desc: 'Mais de uma hora de estudo' },
      ]"
    />
  </div>
</template>

<script>
import DifficultySelector from './DifficultySelector'

export default {
  name: 'DifficultyScreen',
  components: { DifficultySelector },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
