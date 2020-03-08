<template>
  <div>detail</div>
</template>

<script>
export default {
  data() {
    return {};
  },

  methods: {},

  created() {},
  mounted() {
    console.log("$root---", this.$root.$mp.query.id);
    mpvue.request({
      url: `https://m.maizuo.com/gateway/?cinemaId=${
        this.$root.$mp.query.id
      }&k=6820739`,
      header: {
        "X-Client-Info":
          '{"a":"3000","ch":"1002","v":"5.0.4","e":"1583647283532575945257","bc":"110100"}',
        "X-Host": "mall.film-ticket.cinema.info"
      },
      success: ({data:res}) => {
        console.log(res);
      }
    });
  },
  onLoad(options) {
    console.log(options);
  }
};
</script>

<style scoped>
</style>
