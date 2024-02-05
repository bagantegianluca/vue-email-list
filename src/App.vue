<script>
export default {
  name: "App",
  data() {
    return {
      mailList: [],
    };
  },
  mounted() {
    for (let i = 0; i < 10; i++) {
      axios
        .get("https://flynn.boolean.careers/exercises/api/random/mail")
        .then((response) => {
          // success
          console.log(response);
          this.mailList.push(response.data.response);
        });
    }
  },
};
</script>

<template>
  <ul v-if="mailList.length === 10">
    <li v-for="mail in mailList">{{ mail }}</li>
  </ul>
  <div v-else>Loading...</div>
</template>

<style scoped></style>
