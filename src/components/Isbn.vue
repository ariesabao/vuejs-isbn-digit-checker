<template>
  <div class="isbn" v-bind:style="{ 'background-color': bgColor  }">
    <input v-model="msg">
    <br />
    <span v-if="isNotBlank()">
        <h1 v-if="checkDigit()" >
              {{ msg }} <span v-bind:style="{ 'color': tColor }"> is Valid </span>
        </h1>
        <h1 v-else>
              {{ msg }} <span v-bind:style="{ 'color': tColor }"> is Not Valid </span>
        </h1>
      
    </span>
    <span v-else>

    </span>
    
  </div>
</template>

<script>
export default {
  name: 'Isbn',
  data() {
    return {
      msg: '',
      error: 'enter 10-digit only',
      bgColor: 'transparent',
      tColor: 'black'
    }
  },
  methods: {
    isNotBlank: function() {
      return (this.msg.length >= 1) ? true:false;
    },
    checkDigit:  function() {
     var sum,
        weight,
        digit,
        check,
        i;

    this.message = this.msg;

    this.message = this.msg.replace(/[^0-9X]/gi, '');

      var checkInput = (this.message.length != 10) ? true:false
      this.error = checkInput ? this.error: checkDigit

      if (this.message.length == 10) {
          weight = 10;
          sum = 0;
          for (i = 0; i < 9; i++) {
              digit = parseInt(this.message[i]);
              sum += weight*digit;
              weight--;
          }
          check = 11 - (sum % 11);
          if (check == 10) {
              check = 'X';
          }
          
      }
      var checkDigit = (check == this.message[this.message.length-1].toUpperCase()) ? true:false
          this.tColor = checkDigit ? 'green':'red';
          return checkDigit;
    }
  }
}
</script>

<style scoped>

</style>
