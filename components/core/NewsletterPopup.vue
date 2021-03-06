<template>  
      <form @submit.prevent="subscribe(onSuccesfulSubmission)" novalidate>
        <div class="mb10 pt-xs-6">
          
          <base-input            
            type="email"
            name="email"
            v-model="email"
            autocomplete="off"
            :placeholder="$t('E-mail address *')"
            :validations="[
              {
                condition: $v.email.$error && !$v.email.required,
                text: $t('Field is required.')
              },
              {
                condition: !$v.email.email && $v.email.$error,
                text: $t('Please provide valid e-mail address.')
              }
            ]"
          />
        </div>
        <button-full
          class="mb35 d-xs-none"
          type="submit"
          color="primary"
          :disabled="this.$v.$invalid"
          @click.native="$v.email.$touch"
        >
          {{ $t('Subscribe') }}
        </button-full>
      </form>
   
</template>
<script>
import SubscriptionStatus from '@vue-storefront/core/modules/newsletter/mixins/SubscriptionStatus'
import Subscribe from '@vue-storefront/core/modules/newsletter/mixins/Subscribe'
import i18n from '@vue-storefront/i18n'

import ButtonFull from 'theme/components/theme/ButtonFull.vue'

import BaseInput from 'theme/components/core/blocks/Form/BaseInput.vue'

export default {
 
  beforeDestroy () {
    this.$off('validation-error')
  },
  methods: {
    onSuccesfulSubmission (isSubscribed) {
      if (isSubscribed) {
        this.$store.dispatch('notification/spawnNotification', {
          type: 'success',
          message: i18n.t('You have been successfully subscribed to our newsletter!'),
          action1: { label: i18n.t('OK') }
        })
      }

     
    }
  },
  components: {
    ButtonFull,
    BaseInput
  },
  mixins: [
    SubscriptionStatus, Subscribe
  ]
}
</script>