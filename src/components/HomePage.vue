<template>
  <v-container class="main pa-5 px-7">
    <v-row v-if="!dialog">
      <v-col cols="12" class="">
        <div class="circle">
          <v-icon color="" icon="mdi-star" size="large"></v-icon>
        </div>
      </v-col>
      <v-col cols="12" class="py-0 mt-5">
        <div class="text4">How did we do?</div>
      </v-col>
      <v-col cols="12" class="py-0 pt-3">
        <div class="text5">
          Please let us know how we did with your support request. All feedback
          is appreciated to help us improve our offering!
        </div>
      </v-col>

      <v-col cols="12" class="px-14 py-4">
        <div class="circle-container">
          <v-btn
            v-for="n in 5"
            :key="n"
            class="circle2"
            :class="{ selected: selectedRating === n }"
            color=""
            width="50"
            height="50"
            min-width="50"
            min-height="50"
            rounded
            @click="selectRating(n)"
          >
            {{ n }}
          </v-btn>
        </div>
      </v-col>

      <v-col cols="12">
        <v-btn block rounded="xl" class="btn" @click="submitRating"
          >Submit</v-btn
        >
      </v-col>
    </v-row>

    <!-- Dialog for showing the selected rating -->
    <v-dialog v-model="dialog" width="367" height="367" :scrim="false">
      <v-card class="main2" style="border-radius: 20px">
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" class="d-flex justify-center">
                <img
                  class="img3"
                  src="/src/assets/illustration-thank-you.svg"
                  alt=""
                />
              </v-col>
              <v-col cols="12" class="d-flex justify-center">
                <v-chip variant="flat" class="text1" size="default">
                  <div class="mx-2 text-caption">
                    You selected {{ selectedRating }} out of 5
                  </div>
                </v-chip>
              </v-col>
              <v-col cols="12" class="text-h5 text-center text2"
                >Thank you!</v-col
              >
              <v-col cols="12" class="text3 px-1"
                >We appreciate you taking time to give a rating. If you ever
                need more support, don't hesitate to get in touch!</v-col
              >
            </v-row>
          </v-container>
        </v-card-text>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script setup>
import { ref } from "vue";

// Reactive variables
const selectedRating = ref(null);
const dialog = ref(false);

// Method to select a rating
const selectRating = (rating) => {
  selectedRating.value = rating;
};

// Method for submit action
const submitRating = () => {
  if (selectedRating.value !== null) {
    console.log(`Rating submitted: ${selectedRating.value}`);
    // Show dialog or handle feedback submission
    if (selectedRating.value !== null) {
      dialog.value = true; // Open dialog
    }
  } else {
    alert("Choose a rating!!!");
  }
};

const closeDialog = () => {
  dialog.value = false;
};
</script>

<style scoped>
@font-face {
  font-family: f1;
  src: url(/src/assets/Overpass-Regular.ttf);
}
@font-face {
  font-family: f2;
  src: url(/src/assets/Overpass-SemiBold.ttf);
}
.text1 {
  font-family: f1;
  color: hsl(25, 97%, 53%);
  background-color: hsl(210, 19%, 18%);
}
.text2 {
  font-family: f2;
}
.text3 {
  font-family: f1;
  color: hsl(216, 10%, 62%);
  font-size: 13px;
  text-align: center;
}
.text4 {
  font-family: f2;
  font-size: 26px;
}
.text5 {
  font-family: f1;
  color: hsl(216, 10%, 62%);
  font-size: 14px;
}
.main {
  width: 367px;
  height: 367px;
  background-image: linear-gradient(
    to bottom,
    hsl(210, 21%, 17%),
    hsl(212, 24%, 12%)
  );
  border-radius: 20px;
}
.circle {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: hsl(215, 18%, 19%);
  display: flex;
  justify-content: center;
  align-items: center;
}

i.mdi {
  font-size: 24px; /* Size of the icon */
  color: hsl(25, 97%, 53%);
}
.text {
  font-size: 26px;
}
.btn {
  background-color: hsl(25, 97%, 53%);
  color: hsl(43, 60%, 7%);
}
.btn:hover {
  background-color: hsl(0, 0%, 100%);
}

.circle-container {
  display: flex;
  justify-content: center;
  gap: 16px; /* Spacing between buttons */
}

.circle2 {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  color: white;
  border-radius: 50%;
  padding: 0;
  background-color: hsl(210, 19%, 18%);
}
.circle2:hover {
  background-color: hsl(25, 97%, 53%);
}

/* When a circle is selected, change background color to white */
.circle2.selected {
  background-color: white;
  color: black;
}

/* Custom disabled styles */

.img3 {
  width: 50%;
}
.main2 {
  width: 367px;
  height: 367px;
  background-image: linear-gradient(
    to bottom,
    hsl(210, 21%, 17%),
    hsl(212, 24%, 12%)
  );
}
</style>