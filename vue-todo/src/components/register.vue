<template>
  <div class="md-layout-item md-size-33 md-medium-size-50 md-small-size-70 md-xsmall-size-100">
    <md-card>
      <form novalidate @submit.prevent="validateUser">
        <md-card-header>
          <div class="md-title">Register</div>
        </md-card-header>

        <md-card-content>
          <md-field :class="getValidationClass('email')">
            <label for="email">Email</label>
            <md-input
              type="email"
              name="email"
              id="email"
              autocomplete="email"
              v-model="form.email"
              :disabled="sending"
            />
            <span class="md-error" v-if="!$v.form.email.required">The email is required</span>
            <span class="md-error" v-else-if="!$v.form.email.email">Invalid email</span>
          </md-field>

          <md-field :class="getValidationClass('password')">
            <label for="password">Password</label>
            <md-input
              type="password"
              name="password"
              id="password"
              autocomplete="password"
              v-model="form.password"
              :disabled="sending"
            />
            <span class="md-error" v-if="!$v.form.password.required">Password required</span>
            <span class="md-error" v-else-if="!$v.form.password.password">Invalid password</span>
            <span class="md-error" v-else-if="$v.form.password.password != $v.form.confirm.confirm">Passwords do not match</span>
          </md-field>

          <md-field :class="getValidationClass('password')">
            <label for="confirm">Confirm</label>
            <md-input
              type="password"
              name="confirm"
              id="confirm"
              autocomplete="password"
              v-model="form.confirm"
              :disabled="sending"
            />
            <span class="md-error" v-if="!$v.form.confirm.required">Password required</span>
            <span class="md-error" v-else-if="!$v.form.confirm.confirm">Invalid password</span>
          </md-field>

        </md-card-content>

        <md-progress-bar md-mode="indeterminate" v-if="sending"/>

        <md-card-actions>
          <md-button type="submit" class="md-primary" :disabled="sending">Login</md-button>
        </md-card-actions>
      </form>
    </md-card>
  </div>
</template>

<script>
import { validationMixin } from "vuelidate";
import {
  required,
  email
} from "vuelidate/lib/validators";

export default {
  name: "FormValidation",
  mixins: [validationMixin],
  data: () => ({
    form: {
      email: null,
      password: null,
      confirm: null
    },
    remember: false,
    userSaved: false,
    sending: false,
    lastUser: null
  }),
  validations: {
    form: {
      email: {
        required,
        email
      },
      password: {
        required
      },
      confirm: {
        required
      }
    }
  },
  methods: {
    getValidationClass(fieldName) {
      const field = this.$v.form[fieldName];

      if (field) {
        return {
          "md-invalid": field.$invalid && field.$dirty
        };
      }
    },
    clearForm() {
      this.$v.$reset();
      this.form.email = null;
      this.form.password = null;
      this.form.confirm = null;
    },
    saveUser() {
      this.sending = true;

      // Instead of this timeout, here you can call your API
      window.setTimeout(() => {
        this.lastUser = `${this.form.email} ${this.form.password} ${this.form.confirm}`;
        this.userSaved = true;
        this.sending = false;
        this.clearForm();
      }, 1500);
    },
    validateUser() {
      this.$v.$touch();

      if (!this.$v.$invalid) {
        this.saveUser();
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.md-progress-bar {
  position: absolute;
  top: 0;
  right: 0;
  left: 0;
}
</style>
