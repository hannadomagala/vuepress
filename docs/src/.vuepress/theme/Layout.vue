<template>
  <div class="theme-container">
    <Header/>
    <main>
      <h1 class="title">Red</h1>
      <Content/>
      <form 
        action="https://formspree.io/f/xbj"
        method="post"
        @submit="sendForm"
      >
        <input type="text" name="test" v-model.lazy="test" required>
        <input type="submit" value="Send">
      </form>
    </main>
  </div>
</template>

<script>
  import axios from 'axios';
  import Header from '../components/Header';

  export default {
    components: {
        Header
    },
    data: () => ({
      test: ""
    }),
    methods: {
      async sendForm(e) {
        e.preventDefault();

        axios({
          method: e.target.method,
          url: e.target.action,
          data: {
            test: this.test
          }
        })
          .then(res => {
            console.log(res);
          })
          .catch(err => {
            console.log(err);
          })
      }
    }
  }
</script>