<template>
  <v-alert color="#ff5252" class="white--text my-0 mb-3">
    <v-row align="center" justify="center">
      <v-col cols="12" md="8" class="py-0 my-0 text-center">
        Non-habitual resident status?
      </v-col>
      <v-col class="py-0 my-0" cols="6" md="2">
        <v-row align="center" justify="center">
          <div class="mr-3">no</div>
          <v-switch
            class="white--text m-0"
            v-model="hasRNH"
            label=""
            inset
            color="primary"
          ></v-switch>
          <div>yes</div>
        </v-row>
      </v-col>
      <v-col class="py-0 my-0" cols="2" md="1">
        <v-tooltip bottom>
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              @click="
                goToExternal(
                  'https://www.e-konomista.pt/residente-nao-habitual/'
                )
              "
              icon
              v-bind="attrs"
              v-on="on"
            >
              <v-icon color="white">mdi-help-circle </v-icon>
            </v-btn>
          </template>
          <span>What is this?</span>
        </v-tooltip>
      </v-col>
    </v-row>
  </v-alert>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapGetters(["expenses"]),
    hasRNH: {
      get() {
        return this.$store.state.hasRNH;
      },
      set(value) {
        this.$store.commit("setHasRNH", value);
      },
    },
  },
  methods: {
    goToExternal(url) {
      window.open(url);
    },
  },
};
</script>
