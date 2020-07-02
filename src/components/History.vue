<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      {{ currentHistory.content }}
    </p>
    <button v-if="begin" @click="show()">
      chargue
    </button>
    <ul v-if="!begin">
      <li 
        v-for="way in currentHistory.ways"
        v-bind:key="way"
        @click="getNext(way.history_id)"

      >
        {{ way.content }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'History',
  props: {
    msg: String
  },
  data () {
    return {
      historys: [],
      currentHistory: '',
      begin: true,
    }
  },
  mounted () {
    axios
      .get('http://localhost:8080/history')
      .then(response => ( 
        this.historys = response.data.data 
        )
      );
  },
  methods: {
    show() {
      this.currentHistory = this.historys.shift();
      this.begin = false;
    },
    getNext(id) {
      this.currentHistory = this.getHistory(id);
    },
    getHistory(id) {
      return this.historys.find( history => history.id === id);
    }
  },
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
