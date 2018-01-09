<template>
  <div>
    <h2>{{ msg }}</h2> <hr>
    <h3>{{ $store.state.a.count }}</h3>
    <div>
      <button @click="$store.commit('add', 10)">+</button> |
      <button @click="reduce">-</button>
    </div>
    <div>
      <button @click="addAction">+</button> |
      <button @click="reduceAction">-</button>
    </div>
  </div>
</template>

<script>
import store from '../vuex/store.js'
import { mapState, mapMutations, mapGetters, mapActions } from 'vuex'
export default {
  data () {
    return {
      msg: 'hello, vuex'
    }
  },
  // 方法1
  // computed: {
  //   count () {
  //     return this.$store.state.count
  //   }
  // },

  // // 方法2
  // computed: mapState({
  //   count: state => state.count
  // }),

  // 方法3
  // computed: mapState(['count']),
  computed: {
    // 扩展符号...
    // ...mapState(['count']),
    // count () {
    //   // 每加减一次都会先+100
    //   return this.$store.getters.count
    // }
    // ...mapGetters(['count'])
    count () {
      return this.$store.state.a.count
    }
  },
  methods: {
    ...mapMutations(['add', 'reduce']),
    ...mapActions(['addAction', 'reduceAction'])
  },
  store
}
</script>

<style>

</style>
