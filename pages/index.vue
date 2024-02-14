<template>
  <v-app>
    <v-container>
      <v-col col="12" class="pa-4">
        <v-row sm="12" xs="4" md="4" class="bn justify-space-around">
          <div v-if="!happyMessage">
            <img
              src="https://i.pinimg.com/originals/32/84/93/328493509edd6499da6cc4a2b524954f.gif"
              alt="Initial Image"
              width="400"
              height="auto"
            />
            <h1 class="text-center">Will you be my Valentine❤️?</h1>
          </div>

          <div v-if="happyMessage">
            <img
              src="https://i.pinimg.com/originals/1e/31/32/1e31323bae63dd3b0224b75bac7d58a5.gif"
              alt="Happy Image"
              width="400"
              height="auto"
            />
            <h1 class="text-center">
              ຢາກໃຫ້ເຈົ້າມາເປັນສ່ວນຫນຶ່ງໃນຊີວິດຂອງຂ້ອຍ💞
            </h1>
          </div>

          <v-btn
            dark
            v-if="!happyMessage"
            :style="{
              fontSize: fontSize + 'px',
              width: buttonWidth + 'px',
              height: buttonHeight + 'px',
            }"
            color="green"
            @click="showHappyMessage"
            >Yes</v-btn
          >

          <v-btn
            dark
            v-if="!happyMessage"
            color="red"
            @click="increaseSize"
            style="width: 180px; height: 50px; margin-bottom: 10px"
            >{{ noButtonText }}</v-btn
          >
        </v-row>
      </v-col>
    </v-container>

    <v-btn dark color="pink" @click="goToAnotherPage">ເປີດຂອງຂວັນພິເສດ</v-btn>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      color: 'pink',
      fontSize: 14,
      buttonWidth: 180,
      buttonHeight: 50,
      noButtonText: 'No',
      noButtonMessages: [
        'ບໍ່ກົດແທ້ຫວາ😫?',
        'ບໍ່ກົດແທ້ນິ🥺?',
        'ຄິດດີໆ🥺?',
        'ກົດໃຫ້ຂ້ອຍສາ😥',
        'ກົດໃຫ້ແນ່🥺',
        'ນ໊າາາາາາາ🥺',
        'ກົດສາາາາາາ🥺',
      ],
      messageIndex: 0,
      happyMessage: false,
    }
  },
  methods: {
    increaseSize() {
      this.fontSize += 2
      this.buttonWidth += 10
      this.buttonHeight += 10
      this.noButtonText = this.noButtonMessages[this.messageIndex]
      this.messageIndex = (this.messageIndex + 1) % this.noButtonMessages.length
    },
    showHappyMessage() {
      this.happyMessage = true
    },
    goToAnotherPage() {
      // Your code to navigate to another page here
      // For example:
      this.$router.push('/inspire')
    },
  },
}
</script>
<style scoped>
.bn {
  position: absolute;
  top: 15%;
  left: 50%;
  margin-top: -10px;
  margin-left: -40px;
  width: 100px;
  height: 100px;
}
</style>
