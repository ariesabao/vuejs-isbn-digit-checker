<template>
  <div class="isbn">
    <input v-model="msg">
    <br />
    <h1>{{ checkDigit() }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Isbn',
  data() {
    return {
      msg: ''
    }
  },
  methods: {
    checkDigit: function() {
     var sum,
        weight,
        digit,
        check,
        i;

    this.msg = this.msg.replace(/[^0-9X]/gi, '');

    if (this.msg.length != 10) {
        //return false;
    }

    if (this.msg.length == 10) {
        weight = 10;
        sum = 0;
        for (i = 0; i < 9; i++) {
            digit = parseInt(this.msg[i]);
            sum += weight*digit;
            weight--;
        }
        check = 11 - (sum % 11);
        if (check == 10) {
            check = 'X';
        }
        if (check == this.msg[this.msg.length-1].toUpperCase() == true){
          return this.msg + ' is Valid';
        } else {
          return this.msg + ' is Not Valid';
        }
    }
    }
  }
}
</script>

<style scoped>

</style>
