<template>
  <div class="hello">
    <ul>
      <li v-for="item of items.items" :key="item.id">
        {{ item.id }}
        {{ item.name }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data() {
    return {
      items: [],
    }
  },
  async created() {
    try {
      const res = await axios.get(`../data.json`);
      this.items = res.data;
    } catch (error) {
      console.log(error);
    }
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
