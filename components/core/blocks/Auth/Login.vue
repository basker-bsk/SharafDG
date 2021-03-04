<template>
  <div>
    <div class="modal-cross-icon">
      <i
        slot="close"
        class="modal-close material-icons cl-bg-tertiary"
        @click="close"
      >
        close
      </i>
    </div>
    <header class="modal-header-custom">
      <center>Sign in to Sharaf DG</center>
    </header>
    <div v-if="hasRedirect" class="pt10 pb10 px65 redirect-error">
      <p class="h5 mb0 mt0">
        {{ $t('You need to be logged in to see this page') }}
      </p>
    </div>
    <div class="modal-content pb60 px65 bg-cl-white">
      <form @submit.prevent="login" novalidate>
        <base-input
          class="email-or-mobile"
          type="email"
          name="email"
          focus
          v-model="email"
          @blur="$v.email.$touch()"
          :placeholder="$t('Email or Mobile Number')"
          :validations="[
            {
              condition: !$v.email.required && $v.email.$error,
              text: $t('Field is required.')
            },
            {
              condition: !$v.email.email && $v.email.$error,
              text: $t('Please provide valid e-mail address.')
            }
          ]"
        />
        <base-input
          class="mb10 pass-input"
          type="password"
          name="password"
          v-model="password"
          @blur="$v.password.$touch()"
          :placeholder="$t('Password')"
          :validations="[{
            condition: !$v.password.required && $v.password.$error,
            text: $t('Field is required.')
          }]"
        />
        <div class="row h-align-right">
          <div class="col-xs-12 col-sm-12 mb35 flex end-xs middle-xs h-align-right">
            <a href="#" class="forgot-password" @click.prevent="remindPassword">
              {{ $t('Forgot the password?') }}
            </a>
          </div>
        </div>
        <button-full class="button full-button brdr-none w-100 primary primary-full px40" type="submit" data-testid="loginSubmit">
          {{ $t('LOG IN') }}
        </button-full>
        <div class="center-xs request-otp">
          {{ $t('No password? ') }}
          <a href="#" @click.prevent="switchElem" data-testid="requestOTP">
            {{ $t('Request for OTP') }}
          </a>
        </div>
        <div class="center-xs login-with">
          <div class="t-cell"><div>&nbsp;</div></div>
          <div class="t-cell">OR LOG IN WITH</div>
          <div class="t-cell"><div>&nbsp;</div></div>
        </div>
        <div class="row">
          <a class="fb-ic mr-3" role="button"><mdb-icon fab icon="facebook-f" size="lg" /></a>
          <a class="tw-ic mr-3" role="button"><mdb-icon fab icon="twitter" size="lg" /></a>
          <a class="gplus-ic mr-3" role="button"><mdb-icon fab icon="google-plus-g" size="lg" /></a>
        </div>      
        <button-full 
         class="button-outline create-account full-button brdr-none w-100 px40"
         @click.prevent="switchElem"
         data-testid="registerLink">
          {{ $t('CREATE ACCOUNT') }}
        </button-full>
      </form>
    </div>
  </div>
</template>

<script>
import Login from '@vue-storefront/core/compatibility/components/blocks/Auth/Login'

import ButtonFull from 'theme/components/theme/ButtonFull.vue'
import BaseCheckbox from '../Form/BaseCheckbox.vue'
import BaseInput from '../Form/BaseInput.vue'

import { required, email } from 'vuelidate/lib/validators'

export default {
  mixins: [Login],
  validations: {
    email: {
      required,
      email
    },
    password: {
      required
    }
  },
  data () {
    return {
      hasRedirect: !!localStorage.getItem('redirect')
    }
  },
  methods: {
    close (e) {
      if (e) localStorage.removeItem('redirect')
      this.$bus.$emit('modal-hide', 'modal-signup')
    },
    login () {
      if (this.$v.$invalid) {
        this.$v.$touch()
        this.$store.dispatch('notification/spawnNotification', {
          type: 'error',
          message: this.$t('Please fix the validation errors'),
          action1: { label: this.$t('OK') }
        })
        return
      }
      this.callLogin()
    },
    remindPassword () {
      if (!(typeof navigator !== 'undefined' && navigator.onLine)) {
        this.$store.dispatch('notification/spawnNotification', {
          type: 'error',
          message: this.$t('Reset password feature does not work while offline!'),
          action1: { label: this.$t('OK') }
        })
      } else {
        this.callForgotPassword()
      }
    },
    onSuccess () {
      this.$store.dispatch('notification/spawnNotification', {
        type: 'success',
        message: this.$t('You are logged in!'),
        action1: { label: this.$t('OK') }
      })
    },
    onFailure (result) {
      this.$store.dispatch('notification/spawnNotification', {
        type: 'error',
        message: this.$t(result.result),
        action1: { label: this.$t('OK') }
      })
    }
  },
  components: {
    ButtonFull,
    BaseCheckbox,
    BaseInput
  }
}
</script>

<style lang="scss" scoped>
@import '~theme/css/variables/colors';
@import '~theme/css/helpers/functions/color';
$color-error: color(error);
$white: color(white);
$lightblue: color(sdg-lightblue);
$darkblue: color(sdg-darkblue);

  .modal-header{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .modal-close{
    cursor: pointer;
  }
  .modal-content {
    border-radius: 8px;
    @media (max-width: 400px) {
      padding-left: 20px;
      padding-right: 20px;
    }
  }
  .redirect-error {
    background-color: $color-error;
    color: $white;
  }
  .modal-cross-icon {
    text-align: right;
  }
  .modal-cross-icon i {
    margin: 10px;
  }
  /*.email-or-mobile input.border-box {
    outline: none;
    border: 1px solid #bdbdbd;
  }
  .pass-input input.border-box {
    outline: none;
    border: 1px solid #bdbdbd;
  }
  .email-or-mobile input.border-box:hover {
    outline: none;
    border: 1px solid #bdbdbd;
  }
  .pass-input input.border-box:hover {
    outline: none;
    border: 1px solid #bdbdbd;
  }
  .email-or-mobile input.border-box ~ label {
    top: -10px;
    font-size: 14px;
    color: #4dba87;
  }
  .pass-input input.border-box ~ label {
    top: -10px;
    font-size: 14px;
    color: #4dba87;
  }*/
  .email-or-mobile {
    margin-bottom: 25px;
  }
  .pass-input {
    min-height: auto;
  }
  .modal-header-custom {
    margin-bottom: 40px;
    font-size: 20px;
  }
  .modal-content {
    @media (min-width: 600px) {
      margin-right: 50px;
      margin-left: 50px;
    }
  }
  .forgot-password {
    font-size: 14px;
    margin-bottom: 40px;
  }
  .request-otp {
    font-size: 14px;
    margin: 10px 0;
  }
  .login-with {
    font-size: 14px;
    font-weight: 600;
    margin: 30px 0;
    width: 100%;
    display: table;
    .t-cell {
      display: table-cell;
      vertical-align: middle;
      width: 33.2%;
      div {
        background-color: #e1e1e1;
        width: 100%;
        height: 0.5px;
      }
    }
  }
  .create-account {
    border: 1px solid;
    background-color: color(transparent);
    padding-top: 7px;
    padding-bottom: 7px;
    font-size: 10px;
    text-transform: uppercase;
    font-weight: bold;
    letter-spacing: 1px;
    transition: all .2s linear;
    &.w-full {
      width: 100%;
    }
    &.w-200 {
      min-width: 200px;
    }
    

    border-radius: 4px;  
    border-color: $lightblue;
    color: $lightblue;
    &:hover,
    &:focus {
      color: $darkblue;
      border-color: $darkblue;
      text-decoration: none;
    }
  }
</style>
