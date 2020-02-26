<template>
  <div class="hello">
    <div>
      Como está seu tempo?
    </div>
    <div>
      Quanto mais longa sua sessão de estudos, mais rápido irá aprender!
    </div>
    <DifficultySelector :items="[{header: 'Curtinho', desc: '15 a 30 minutos de estudo'}]"/>
  </div>
</template>

<script>
import DifficultySelector from './DifficultySelector'


export default {
  name: 'DifficultyScreen',
  components: {DifficultySelector},
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
