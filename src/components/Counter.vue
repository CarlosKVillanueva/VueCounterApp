<template>
	<h2>{{ customTitle }}</h2>
	<p> {{ counter }} </p>
	<div>
		<p>{{ counter }} <sup>2</sup> = {{ squareCounter }}</p>
	</div>

	<div>
		<button v-on:click="decrease"> - 1</button>
		<button @click="increase"> + 1</button>

	</div>
</template>

<script>
export default {
	props:{
		title: String,
		start: {
			type: Number,
			// require: true,
			default: 10,
			validator( value ) {
				return value > 100
			},
		},
	},
	data() {
		return {
			counter: this.start,
		};
	},
	methods: {
		getSquareValue() {
			return this.counter * this.counter;
		},
		increase() {
			this.counter++;
		},
		decrease() {
			this.counter--;
		},
	},
	computed: {
		squareCounter() {
			return this.counter * this.counter;
		},
		customTitle() {
			return this.title || 'Cuounter';
		},
	}
}
</script>

<style scoped>

button {
	background-color: #64BB87;
	border-radius: 5px;
	color: white;
	cursor: pointer;
	margin: 0 5px;
	padding: 5px 15px;
	transition: 0.3s ease-in-out;
}

button:hover {
	background-color: #5aa67b;
	transition: 0.3s ease-in-out;
}
</style>