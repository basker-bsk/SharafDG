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
      <center v-show="emailFormSubmit == false && mobileFormSubmit == false">Create Account</center>
      <center v-show="emailFormSubmit == true">Verify Email Address</center>
      <center v-show="mobileFormSubmit == true">Verify Mobile Number</center>
      
    </header>

    
    <div v-show="emailFormSubmit == false && mobileFormSubmit == false" class="modal-content pb60 px65">
      
      <div class="custom-tab-header">
        <div class="tab-title" :class="selectedTab == 'tab-mobile' ? ' active' : ''" id="tab-mobile" @click="changeTab">MOBILE</div>
        <div class="tab-title" :class="selectedTab == 'tab-email' ? ' active' : ''" id="tab-email" @click="changeTab">EMAIL</div>
      </div>
      
      <div v-show="selectedTab === 'tab-mobile'">
        <form @submit.prevent="continueMobile" novalidate>
          <base-input
            class=""
            type="tel"
            name="mobile"
            autocomplete="mobile"
            prefixdata=true
            :placeholder="$t('Mobile Number')"
            :validations="[
              
            ]"
          />
          <div class="terms-privacy">
            By clicking continue you are agreeing to the SharafDG
            <br />
            <a class="" href="#" >
              {{ $t('Terms & Conditions') }}
            </a> 
            and 
            <a class="" href="#">
              {{ $t('Privacy Policy') }}
            </a>
          </div>

          <button-full class="button full-button brdr-none w-100 primary primary-full px40" type="submit">
            {{ $t('COUNTINUE') }}
          </button-full>
          <div class="center-xs">
            <span>
              <a href="#" class="login-now" @click.prevent="switchElem">
                {{ $t('Login Now') }}
              </a>
            </span>
          </div>
        </form>
      </div>
      <div v-show="selectedTab === 'tab-email'">
        <form @submit.prevent="continueEmail" novalidate>
          
          
            <base-input
              class="mb10"
              type="text"
              name="first-name"
              autocomplete="given-name"
              v-model="firstName"
              @blur="$v.firstName.$touch()"
              :placeholder="$t('First Name')"
              :validations="[
                {
                  condition: !$v.firstName.required && $v.firstName.$error,
                  text: $t('Field is required.')
                },
                {
                  condition: !$v.firstName.minLength,
                  text: $t('Name must have at least 2 letters.')
                },
                {
                  condition: !$v.firstName.alpha && $v.firstName.$error,
                  text: $t('Accepts only alphabet characters.')
                }
              ]"
            />
            <base-input
              class="mb10"
              type="text"
              name="last-name"
              autocomplete="last-name"
              v-model="lastName"
              @blur="$v.lastName.$touch()"
              :placeholder="$t('Last Name')"
              :validations="[
                {
                  condition: !$v.lastName.required && $v.lastName.$error,
                  text: $t('Field is required.')
                },
                {
                  condition: !$v.lastName.alpha && $v.lastName.$error,
                  text: $t('Accepts only alphabet characters.')
                }
              ]"
            />
          <base-input
            class="mb10"
            type="email"
            name="email"
            autocomplete="email"
            v-model="email"
            @blur="$v.email.$touch()"
            focus
            :placeholder="$t('Email')"
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
            class=""
            type="password"
            name="password"
            ref="password"
            autocomplete="new-password"
            v-model="password"
            @blur="$v.password.$touch()"
            :placeholder="$t('Password')"
            :validations="[
              {
                condition: !$v.password.required && $v.password.$error,
                text: $t('Field is required.')
              },
              {
                condition: !$v.password.minLength && $v.password.$error,
                text: $t('Password must have at least 8 letters.')
              }
            ]"
          />
          <div class="terms-privacy">
            By clicking continue you are agreeing to the SharafDG
            <br />
            <a class="" href="#" >
              {{ $t('Terms & Conditions') }}
            </a> 
            and 
            <a class="" href="#">
              {{ $t('Privacy Policy') }}
            </a>
          </div>
          
          <button-full class="button full-button brdr-none w-100 primary primary-full px40" type="submit">
            {{ $t('COUNTINUE') }}
          </button-full>
          <div class="center-xs">
            <span>
              <a class="login-now" href="#" @click.prevent="switchElem">
                {{ $t('Login Now') }}
              </a>
            </span>
          </div>
        </form>
      </div>
    </div>

    <div v-show="mobileFormSubmit === true|| emailFormSubmit === true" class="modal-content pb60 px65">
      <p class="otp-message">
        Please insert the One Time Password (OTP) that we have sent to 
        <b v-show="mobileFormSubmit === true">9123456789</b> 
        <b v-show="emailFormSubmit === true">sharafdg@gmail.com</b>
        in order to verify your number.
      </p>
      <p class="resend-message">Resend in 1:00</p>
      
      <div class="row">
          
        <base-input
          class="col-xs-2"
          type="text"
          name="otp1"
        />
        <base-input
          class="col-xs-2"
          type="text"
          name="otp2"
        />
      
        <base-input
          class="col-xs-2"
          type="text"
          name="otp3"
        />
        <base-input
          class="col-xs-2"
          type="text"
          name="otp4"
        />
      
        <base-input
          class="col-xs-2"
          type="text"
          name="otp5"
        />
        <base-input
          class="col-xs-2"
          type="text"
          name="otp6"
        />

        <button-full class="button full-button brdr-none w-100 primary primary-full px40" type="submit">
          {{ $t('SUBMIT') }}
        </button-full>
        
      </div>
    </div>

  </div>
</template>
<script>
import Register from '@vue-storefront/core/compatibility/components/blocks/Auth/Register'
import ButtonFull from 'theme/components/theme/ButtonFull.vue'
import BaseCheckbox from 'theme/components/core/blocks/Form/BaseCheckbox.vue'
import BaseInput from 'theme/components/core/blocks/Form/BaseInput.vue'
import { required, email, minLength, sameAs, alpha } from 'vuelidate/lib/validators'

export default {
  validations: {
    email: {
      required,
      email
    },
    firstName: {
      minLength: minLength(2),
      required,
      alpha
    },
    lastName: {
      required,
      alpha
    },
    password: {
      minLength: minLength(8),
      required
    },
    rPassword: {
      required,
      sameAsPassword: sameAs('password')
    },
    conditions: {
      sameAs: sameAs(() => true)
    }
  },
  mixins: [Register],
  components: {
    ButtonFull,
    BaseCheckbox,
    BaseInput
  },
  data () {
    return {
      selectedTab: "tab-mobile",
      mobileFormSubmit: false,
      emailFormSubmit: false
    }
  },
  methods: {
    changeTab: function(event) {
        var targetId = event.currentTarget.id;
        this.selectedTab = targetId;
    },
    continueEmail: function() {
      this.emailFormSubmit = true;
      this.mobileFormSubmit = false;
    },
    continueMobile: function() {
      this.emailFormSubmit = false;
      this.mobileFormSubmit = true;
    },
    register () {
      if (this.$v.$invalid) {
        this.$v.$touch()
        this.$store.dispatch('notification/spawnNotification', {
          type: 'error',
          message: this.$t('Please fix the validation errors'),
          action1: { label: this.$t('OK') }
        })
        return
      }
      this.callRegister()
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
  }
}

</script>

<style lang="scss" scoped>
  .modal-header{
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .modal-close{
    cursor: pointer;
  }
  .modal-content {
    @media (max-width: 400px) {
      padding-left: 20px;
      padding-right: 20px;
    }
  }
  .custom-tab-header {
    text-align: center;
    margin-bottom: 40px;
  }
  .otp-message {
    font-size: 13px;
    text-align: center;
    margin: 0 auto;
    @media (max-width: 600px) {
      width: 85%;
    }
  }
  .resend-message {
    font-size: 14px;
    margin: 30px 0;
    text-align: center;
    font-weight: bold;
  }
  .tab-title {
    display: inline-block;
    border-bottom: 2px solid #bdbdbd;
    font-size: 14px;
    padding: 0 25px 10px 25px;
    font-weight: 700;
    color: #8e8e8e;
    cursor: pointer;
  }
  .tab-title.active {
    color: #000000;
    border-color: #ffa900;
  }
  #tab-email {
    margin-left: -4px;
  }
  .login-now {
    font-size: 14px;
    margin-top: 20px;
    display: inline-block;
  }
  .terms-privacy {
    font-size: 13px;
    margin-bottom: 20px;
  }
  .modal-cross-icon {
    text-align: right;
  }
  .modal-cross-icon i {
    margin: 10px;
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
</style>
