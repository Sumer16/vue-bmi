<template>
  <v-container class="flex align-center justify-center flex-column">
    <v-row class="text-center">

      <v-col>
        <h1 class="font-weight-bold mb-3">
          Let's Calculate your BMI
        </h1>

        <p class="subheading font-weight-regular">
          Please Enter your Height(mts) & Weight(kg)
        </p>

        <v-text-field
            v-model="height"
            label="Height(M)"
            :rules="[numberRule]"
            required
          ></v-text-field>

          <v-text-field
            v-model="weight"
            label="Weight(Kg)"
            :rules="[numberRule]"
            required
          ></v-text-field>

          <v-card-actions v-on:click="calBMI">
          <v-btn
            text
            color="deep-purple accent-4"
          >
            Calculate
          </v-btn>
        </v-card-actions>

        <h1 v-if="result">{{ result }} kg/m<sup>2</sup></h1>
        <p>{{ weigh }}</p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        height: '',
        weight: '',
        result: '',
        weigh: '',
        numberRule: v  => {
          if (!v.trim()) return true;
          if (!isNaN(parseFloat(v)) && v >= 0 && v <= 444) return true;
          return 'Number has to be between 0 and 444';
        },
      }
    },
    methods: {
      calBMI() {
        let result = this.weight / Math.pow(this.height, 2);
        this.result = +result.toFixed(2);
        if (this.result < 18.5) {
          this.weigh = 'Underweight';
        } else if (18.51 < this.result && this.result < 24.99) {
          this.weigh = 'Normal';
        } else if (25 < this.result && this.result < 29.99) {
          this.weigh = 'Overweight';
        } else if (30 < this.result){
          this.weigh = 'Obesity';
        } else {
          this.weigh = 'Please enter proper values!';
        }
      }
    }
  }
</script>
