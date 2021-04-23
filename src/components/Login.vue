<template>
  <div class='login'>
    <div class='login__title'>
      Log in<br />
      with EdgeKit
    </div>
    <div class='login__email'>
      <input type="email" :class="`login__input ${isValidEmail ? '': 'login__input__invalid'}`" placeholder="Work email" v-model="email" />
      <label v-if="inputedEmail && !isValidEmail" class='login__input__invalid_text'>This is email is badly <br/> formatted.</label>
    </div>
    <div class='login__email'>
      <input type="password" :class="`login__input ${isValidPass ? '': 'login__input__invalid'}`" placeholder="Password" v-model="pass" />
      <label v-if="inputedPass && !isValidPass" class='login__input__invalid_text'>The password is invalid or the <br/> user doesn’t have a password.</label>
      <div v-if="inputedPass && !isValidPass" class='login__horizontal__divider'></div>
      <a href="#" class='login__pass__forgot'>Forgot <br/> password?</a>
    </div>
    <button class='login__submit' :disabled="!(isValidEmail && isValidPass && inputedPass && inputedEmail)" @click="onSubmit">Log in</button>
  </div>
</template>

<script lang="ts">
// import { watch } from '@vue/runtime-core';
import { Watch } from 'vue-property-decorator';
import { Options, Vue } from 'vue-class-component';

@Options({
  props: {
    msg: String
  }
})
export default class Login extends Vue {
  msg!: string
  email: string = ''
  pass: string = ''
  isValidEmail: boolean = true
  isValidPass: boolean = true
  inputedEmail: boolean = false
  inputedPass: boolean = false

  @Watch('email')
  onEmailChanged(value: string) {
    this.inputedEmail = true
    if(value !== '' && /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(value)) this.isValidEmail = true
    else this.isValidEmail = false
  }

  @Watch('pass')
  onPassChanged(value: string) {
    this.inputedPass = true
    if(value !== '' ) this.isValidPass = true
    else this.isValidPass = false
  }

  onSubmit() {
    console.log('submitted')
    this.$router.push({ name: 'Home' })
  }
}
</script>

<style scoped>
.login {
  margin: 80px auto auto 328px;
  text-align: left;
}
.login__title {
  font-family: Inter;
  font-style: normal;
  font-weight: bold;
  font-size: 48px;
  line-height: 56px;
  letter-spacing: -0.02em;
  text-align: left;
  color: #171717;
  margin-bottom: 40px;
}
.login__email {
  display: flex;
  margin: 20px 0;
  align-items: center;
}
.login__input {
  width: 512px;
  height: 64px;
  background: #FFFFFF;
  box-sizing: border-box;
  border: 1px solid #D6D6D6;
  border-radius: 6px;
  font-size: 18px;
  padding: 24px;
  outline: none !important;
}
.login__input:disabled {
  background: #F4F4F4;
}
.login__input:focus {
  border: 1px solid #2C5EF6;
}
.login__input__invalid {
  border: 1px solid #E84141;
  outline: none;
}
.login__input__invalid_text {
  width: 199px;
  height: 36px;
  font-weight: 500;
  font-size: 14px;
  line-height: 18px;
  letter-spacing: -0.02em;
  color: #E84141;
  margin: auto 40px;
}
.login__horizontal__divider {
  height: 48px;
  border: 1px solid #D6D6D6;
  margin: 0;
}
.login__pass__forgot {
  text-decoration: none;
  width: 71px;
  height: 36px;
  font-weight: 500;
  font-size: 14px;
  line-height: 18px;
  color: #2C5EF6;
  margin: auto 40px;
}
.login__submit {
  width: 512px;
  height: 64px;
  background: #171717;
  color: white;
  border-radius: 6px;
}

button:disabled,
button[disabled]{
  border: none;
  background-color: #cccccc;
}
button:hover {
  background: #2C5EF6;
}
</style>