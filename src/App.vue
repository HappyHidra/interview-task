<template>
	<div class="container">
		<ul class="list list-reset">
			<ChangeForm v-if="popupOpen" @cancelClicked="closePopup" @acceptClicked="(value) => changeItem(value)" :item="currentItem" />
			<li @click="openPopup(item, index)" v-for="(item, index) of list" class="list__item" :key="item.value + index">
				<p class="list__item-name">
					{{ item.name }}
				</p>
				<span type="text" class="list__item-input">{{ item.value }}</span>
			</li>
		</ul>
	</div>
</template>

<script>
	// import list from '@/data/list';
	import ChangeForm from '@/components/ChangeForm.vue';

	export default {
		components: { ChangeForm },
		data() {
			return {
				list: [
					{
						name: 'foo1',
						value: 'bar1',
					},
					{
						name: 'foo2',
						value: 'bar2',
					},
					{
						name: 'foo3',
						value: 'bar3',
					},
					{
						name: 'foo4',
						value: 'bar4',
					},
				],
				popupOpen: false,
				currentItem: null,
				currentItemIndex: 0,
			};
		},
		methods: {
			changeItem(changedItem) {
				this.popupOpen = false;
				this.list[this.currentItemIndex] = changedItem;
			},
			openPopup(item, index) {
				this.popupOpen = true;
				this.currentItem = item;
				this.currentItemIndex = index;
			},
			closePopup() {
				this.popupOpen = false;
			},
		},
	};
</script>

<style>
	* {
		box-sizing: border-box;
	}

	.container {
		margin: 0;
		padding-top: 100px;
		padding-left: 50px;
		padding-right: 50px;
	}

	.list {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
	}

	.list-reset {
		text-decoration: none;
		list-style: none;
	}

	.list__item {
		padding: 10px;
		margin-bottom: 20px;
		border: 1px solid black;
		width: 100px;
		height: 100px;
		background-color: aquamarine;
	}

	.list__item:not(:last-child) {
		margin-right: 40px;
	}

	.list__item-name {
		margin: 0;
		margin-bottom: 20px;
		text-align: center;
		font-size: 24px;
	}

	.list__item-input {
		margin: 0;
		text-align: center;
		width: 100%;
	}
</style>
