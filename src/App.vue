<script>
export default {
  name: "App",
  data() {
    return {
      mailList: [],
    };
  },
  mounted() {
    const axiosRequests = [];

    for (let i = 0; i < 10; i++) {
      axiosRequests.push(
        axios.get("https://flynn.boolean.careers/exercises/api/random/mail")
      );
    }

    Promise.all(axiosRequests)
      .then((responses) => {
        this.mailList = responses.map((response) => response.data.response);
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
      });
  },
};
</script>

<template>
  <ul>
    <li v-for="mail in mailList">{{ mail }}</li>
  </ul>
</template>

<style scoped></style>
