<template>
  <div class='navbar'>
    <img class='navbar__logo' src="../assets/logo.png" alt="Vue logo">
    <div class='navbar__signup'>
      <label>New User? </label>
      <label class='navbar__signup__link'> Sing up</label>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    msg: String
  }
})
export default class Navbar extends Vue {
  msg!: string
}
</script>

<style scoped>
.navbar {
  height: 72px;
  width: 100%;
  background-color: white;
  display: flex;
  justify-content: space-between;
}
.navbar__logo {
  width: 34px;
  height: 28px;
  margin: 22px 0 0 32px;
}
.navbar__signup {
  font-family: Inter;
  font-weight: 400;
  font-size: 16px;
  line-height: 18px;
  color: #A8A8A8;
  align-items: center;
  margin: auto 32px;
}
.navbar__signup__link {
  font-weight: 500;
  color: black;
}

</style>
