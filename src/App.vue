<template>
	<div>
		<month-gallery/>

		<currencies-widget/>

		<balance-widget/>
	</div>
</template>

<script>
import MonthGallery from '@/components/MonthGallery'
import CurrenciesWidget from '@/components/CurrenciesWidget'
import BalanceWidget from '@/components/BalanceWidget'

export default {
	name: 'App',
	components: { MonthGallery, CurrenciesWidget, BalanceWidget }
}
</script>

<style lang="scss">
@import '@/assets/scss/vars.scss';
* {
	outline: none;
	text-decoration: none;
	color: $lightTextColor;
}
body {
background-color: #121217;
}
#app {
	
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
