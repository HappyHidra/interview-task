<template>
	<div class="container">
		<p>{{ currentItem.name }}</p>
		<input type="text" name="" id="" v-model="currentItem.value" />
		<button @click="acceptClicked">Принять</button>
		<button @click="cancelClicked">Отмена</button>
	</div>
</template>

<script>
	export default {
		props: ['item'],
		data() {
			return {
				currentItem: {
					name: this.item.name,
					value: this.item.value,
				},
			};
		},
		methods: {
			cancelClicked() {
				this.$emit('cancelClicked');
			},
			acceptClicked() {
				this.$emit('acceptClicked', this.currentItem);
			},
		},
	};
</script>
