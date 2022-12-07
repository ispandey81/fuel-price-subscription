<script>
import { BASE_SERVICE_URL } from "../constants";
export default {
  data: () => ({
    subscriptions: [],
    form_submitted: false,
    valid: true,
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
  }),
  methods: {
    submit() {
      fetch(
        BASE_SERVICE_URL +
          "getSubscriptionsByEmail?" +
          new URLSearchParams({
            email: this.email,
          }),
        {
          method: "GET",
        }
      )
        .then((response) => response.json())
        .then((data) => {
          this.subscriptions = data;
          this.form_submitted = true;
          this.$refs.form.reset();
        })
        .catch(() => {});
    },
    getDescription(productId) {
      switch (productId) {
        case 1:
          return "Unleaded Petrol (U91)";
        case 2:
          return "Premium Unleaded (U95)";
        case 4:
          return "Diesel";
        case 5:
          return "LPG";
        case 6:
          return "98 RON (U98)";
        case 10:
          return "E85";
        case 11:
          return "Brand diesel";
        default:
          break;
      }
    },
    deleteSubscription(subscriptionId, index) {
      fetch(
        BASE_SERVICE_URL +
          "deleteSubscription?" +
          new URLSearchParams({
            id: subscriptionId,
          }),
        {
          method: "DELETE",
        }
      )
        .then((response) => response.json())
        .then(() => {
          this.form_submitted = false;
          this.subscriptions.splice(index, 1);
        })
        .catch(() => {});
    },
    home() {
      this.$router.push("/");
    },
  },
};
</script>
<template>
  <h2><strong>Unsubscribe from daily emails</strong></h2>
  <br />
  <template v-if="form_submitted && subscriptions.length === 0">
    <v-alert text="No subscriptions found" color="error"></v-alert>
    <br />
    <br />
  </template>
  <v-btn color="success" @click="home">Home page</v-btn>
  <br />
  <br />
  <v-form ref="form" v-model="valid" lazy-validation>
    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      hint="Provide the email used for creating the subscription"
      persistent-hint
      required
    ></v-text-field>
    <br />

    <v-btn color="success" class="mr-4" @click="submit" :disabled="!valid">
      Unsubscribe
    </v-btn>
    <br />
    <br />
    <template v-for="(item, index) in subscriptions" :key="item">
      <p>
        <strong>Subscription details for {{ item.email }}</strong>
      </p>
      <v-card>
        <!-- <v-card-title>Subscription details for {{ item.email }}</v-card-title> -->
        <v-text-field>Suburb: {{ item.suburb }}</v-text-field>
        <v-text-field
          >Fuel type: {{ getDescription(item.product) }}</v-text-field
        >
        <v-card-actions>
          <v-btn
            color="error"
            variant="flat"
            @click="deleteSubscription(item.id, index)"
            >Delete</v-btn
          >
        </v-card-actions>
      </v-card>
      <br />
    </template>
  </v-form>
</template>