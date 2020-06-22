<template>
  <h1>{{ msg }}</h1>
  <button @click="count -= 3">count is: {{ count }}</button>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    
  },
  data() {
    return {
      count: 0
    }
  },
}
</script>
