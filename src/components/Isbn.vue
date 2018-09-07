<template>
  <div class="isbn">
    <template>
       <input placeholder="Enter ISBN #" v-model="msg" >
    <br />
    </template>
    <template v-if="isNotBlank()">
        <template v-if="checkDigit()" >
              {{ msg }} is <span v-bind:style="{ 'color': tColor }">  Valid </span>
        </template>
        <template v-else>
              {{ msg }} is<span v-bind:style="{ 'color': tColor }">  Not Valid </span>
        </template>
      
    </template>
    <template v-else>
       
    </template>
    
  </div>
</template>

<script>
export default {
  name: 'Isbn',
  data() {
    return {
      msg: '',
      error: 'enter 10-digit only',
      tColor: '#ff0000'
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

      if(this.message.length != 10) {
        var checkDigit = (check == this.message[this.message.length-1].toUpperCase()) ? true:false
          this.tColor = checkDigit ? '#008000':'#ff0000';
          return checkDigit;
      }

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
          var checkDigit = (check == this.message[this.message.length-1].toUpperCase()) ? true:false
          this.tColor = checkDigit ? '#008000':'#ff0000';
          return checkDigit;
      }

      
    }
  }
}
</script>

<style scoped>

</style>
