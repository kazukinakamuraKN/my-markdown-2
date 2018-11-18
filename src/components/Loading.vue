<template>
  <div id="loading">
    <p>{{msg}}</p>
  </div>
</template>

<script>
  export default {
  	name: "loading",
  	data() {
  		return {
  			msg: "読み込んでいます"
  		};
  	}
  }
</script>