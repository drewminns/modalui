<template>
  <div class="signupform">
    <div class="signupform__container">
      <h2>Sign up to Dribble</h2>
      <div class="signupform__social">
        <Button
          content="Sign up with Google"
          @clicked="onClickGoogle"
          icon="google"
          variant="secondary"
        />
        <Button
          content="Sign up with Facebook"
          :iconOnly="true"
          icon="facebook-square"
          @clicked="onClickFacebook"
          variant="common"
        />
        <Button
          content="Sign up with Twitter"
          :iconOnly="true"
          icon="twitter"
          variant="common"
          @clicked="onClickTwitter"
        />
      </div>
      <div class="divider"></div>
      <form class="signupform__form" @submit.prevent="handleSubmit">
        <div class="signupform__row">
          <InputField
            label="Full Name"
            name="fullname"
            v-model="fullName"
          />
          <InputField
            label="Username"
            name="username"
            v-model="username"
          />
        </div>
        <div class="signupform__row">
          <InputField
            label="Email Address"
            type="email"
            name="emailaddress"
            v-model="emailAddress"
          />
        </div>
        <div class="signupform__row">
        <InputField
          label="Password"
          type="password"
          name="password"
          placeholder="6+ Characters"
          v-model="password"
        />
        </div>
        <div class="signupform__consent">
        <InputCheckbox
          label="Creating an account means you’re okay with our <a href='#'>Terms of Service</a>, <a href='#'>Privacy Policy</a>, and our default <a href='#'>Notification Settings</a>."
          name="consent"
          v-model="consent"
        />
        </div>
        <Button content="Continue" type="submit" :fullWidth="true"/>
      </form>
    </div>
    <div class="signupform__member">
      <p>Already a member? <a href="#">Sign in</a></p>
    </div>
  </div>
</template>

<script>
import InputField from '@/components/inputField';
import InputCheckbox from '@/components/inputCheckbox';
import Button from '@/components/button';

export default {
  name: 'SignUpForm',
  data () {
    return {
      errors: [],
      fullName: '',
      username: '',
      emailAddress: '',
      password: '',
      consent: false,
    };
  },
  components: {
    InputField,
    InputCheckbox,
    Button,
  },
  methods: {
    onClickGoogle () {
      console.log('Signing with Google');
    },
    onClickFacebook () {
      console.log('Signing with Facebook');
    },
    onClickTwitter () {
      console.log('Signing with Twitter');
    },
    handleSubmit () {
      const { fullName, username, emailAddress, password, consent, } = this;
      if (!fullName && username && emailAddress && password && consent) {
        console.log('Submitting Form');
      }
    },
  },
};
</script>

<style lang="scss" scoped>
  .signupform {

    @include lg {
      margin: auto;
      padding-bottom: 65px;
    }

    &__container {
      width: 100%;
      max-width: 416px;
      margin: auto;
      position: relative;
    }

    &__row {
      display: flex;
    }

    &__consent {
      margin: 6px 0 24px;
    }

    &__member {
      text-align: center;

      @include lg {
        position: absolute;
        right: 48px;
        top: 48px;
      }
    }

    &__social {
      display: flex;
      margin-bottom: calculateRem(30px);

      .button:first-of-type {
        flex-grow: 1;
      }
    }
  }

  .divider {
    margin-bottom: calculateRem(30px);
    position: relative;
    text-align: center;

    &::before {
      content: '';
      display: block;
      height: 1px;
      background: $gray1;
    }

    &::after {
      content: 'Or';
      display: inline-block;
      color: $gray5;
      background: $white;
      padding: 0 calculateRem(16px);
      position: absolute;
      top: -8px;
      left: calc(50% - 25px);
    }
  }
</style>
