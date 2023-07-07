<template>
	<div class="overlay">
		<form class="main-form">
			<p class="main-form__title">{{ currentItem.name }}</p>
			<input class="main-form__input" type="text" name="" id="" v-model="currentItem.value" />
			<div class="main-form__group">
				<button class="btn btn-reset button_success" @click="acceptClicked">Принять</button>
			</div>
			<div class="main-form__group">
				<button class="btn btn-reset button_cancel" @click="cancelClicked">Отмена</button>
			</div>
		</form>
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

<style>
	.overlay {
		position: fixed;
		overflow: hidden;
		top: 0;
		left: 0;
		width: 100%;
		height: 100vh;
		backdrop-filter: blur(10px);
	}

	.main-form {
		position: absolute;
		top: 25%;
		left: 0;
		right: 0;
		padding: 20px;
		display: flex;
		flex-direction: column;
		width: 300px;
		min-height: 300px;
		margin-left: auto;
		margin-right: auto;
		justify-content: center;
		background: #1b1b1b;
		color: #fff;
		box-shadow: #e9204f 0px 5px 15px;
	}

	.main-form__title {
		margin: 40px 0 20px 0;
		font-size: 20px;
		color: #fff;
		user-select: none;
	}

	.main-form__input {
		position: relative;
		display: block;
		margin-bottom: 20px;
		padding: 10px 0 10px 20px;
		height: 45px;
		border: 0;
		outline: 0;
		top: -2px;
		color: #fff;
		font-weight: 700;
		background: rgb(28, 30, 33);
		box-shadow: inset -100px -100px 0 rgb(28, 30, 33);
	}

	.main-form__group {
		display: flex;
	}

	.button-reset {
		padding: 0;
		border: none;
		background-color: transparent;
	}

	.btn {
		display: inline-block;
		padding: 10px;
		margin-bottom: 10px;
		width: 100%;
		border: none;
		outline: none;
		text-align: center;
		color: #fff;
		background: #000;
		cursor: pointer;
		user-select: none;
		font-weight: 700;
		transition: background-color 0.3s ease-in-out, border-color 0.3s ease-in-out;
	}

	.btn:hover {
		background-color: #e9204f;
	}
</style>
