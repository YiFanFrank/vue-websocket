<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      webSocket
    </ul>
  </div>
</template>

<script>
import {mapGetters} from 'vuex'
import io from 'socket.io-client'
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  created() {
    const that = this
    // 连接websocket地址
    this.socket = io.connect('http://172.25.3.30:1080')
    this.getsocket.on('message', function(obj) {
      that.$store.commit('123', obj)
    })
  },
  mounted() {
    this.add()
  },
  methods: {
    add() {
      console.log('socket')
    }
  },
  computed: {
      ...mapGetters([
        'getsocket'
      ])
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
