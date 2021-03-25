<template>
	<nav id="navbar">
  </nav>
</template>

<script>
export default {
	name: 'Navbar',
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/properties';
// $yellow;
// $light-green;
// $green;
// $dark-green;
// $padding-main;

#navbar {
	position: fixed;
	background: #000;
	width: 55vw;
	height: 50px;
	right: 0;
	background: $light-green;
	border-radius: 0px 0px 0px 200px;
}
</style>