<template>
  <div class="messages">
    <p class="advanced" v-if="this.messages.advanced.length">{{[...this.messages.advanced]}}</p>
    <p class="violations" v-if="this.messages.violation.length">violation {{this.messages.violation}}</p>
    <p class="errors" v-if="this.messages.errors.length">Alert : {{this.messages.errors}}</p>
  </div>
</template>
<!-- ========================================================== -->
<script>
import { mapGetters } from "vuex";
export default {
  name: "MessageBox",
  display: "MessageBox",
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["messages"])
  }
};
</script>
<!-- ========================================================== -->
<style scoped>
.messages{
  display: flex;
}
.violations{
  padding:10px;
  background: #6D8AE4;
  color:white;
  border: 0.5px solid grey ;
  border-radius:10px;
 
}
.advanced{
  padding:10px;
  background:#449651;
  color:white;
  border: 0.5px solid grey ;
  border-radius:10px;
 
}
</style>
