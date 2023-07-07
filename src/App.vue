<template>
	<div class="container">
		<ChangeForm v-if="popupOpen" @cancelClicked="closePopup" @acceptClicked="(value) => changeItem(value)" :item="currentItem" />
		<ul class="list list-reset">
			<li @click="openPopup(item, index)" v-for="(item, index) of list" class="list__item" :key="item.value + index">
				<article class="main-card">
					<h3 class="main-card__title">{{ item.name }}</h3>
					<div class="main-card__underline"></div>
					<p class="main-card__descr">
						{{ item.value }}
					</p>
				</article>
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
					{
						name: 'foo5',
						value: 'bar5',
					},
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
					{
						name: 'foo5',
						value: 'bar5',
					},
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
					{
						name: 'foo5',
						value: 'bar5',
					},
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
					{
						name: 'foo5',
						value: 'bar5',
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
				document.body.classList.remove('modal-open');
				this.list[this.currentItemIndex] = changedItem;
			},
			openPopup(item, index) {
				this.popupOpen = true;
				document.body.classList.add('modal-open');
				this.currentItem = item;
				this.currentItemIndex = index;
			},
			closePopup() {
				this.popupOpen = false;
				document.body.classList.remove('modal-open');
			},
		},
	};
</script>

<style>
	* {
		box-sizing: border-box;
	}

	body {
		min-height: 100vh;
		margin: 0;
		padding: 0;
		font-family: Trebuchet MS;
		background: #000;
	}

	body.modal-open {
		overflow: hidden;
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
		justify-content: space-around;
	}

	.list-reset {
		text-decoration: none;
		list-style: none;
	}

	.list__item {
		margin-bottom: 20px;
		padding: 30px;
		width: 22%;
		min-height: 200px;
		background: #1b1b1b;
		cursor: pointer;
		user-select: none;
		transition: background-color 0.3s ease-in-out;
	}

	.list__item:hover {
		background: #e9204f;
		box-shadow: #e9204f 0px 5px 15px;
	}

	.list__item:not(:nth-child(4n)) {
		margin-right: 15px;
	}

	.main-card__title {
		margin: 40px 0 0 0;
		font-size: 20px;
		color: #fff;
	}

	.main-card__underline {
		height: 0;
		width: 35px;
		border-top: 2px solid #e9204f;
		margin-top: 10px;
		transition: border 0.3s ease-in-out;
	}

	.list__item:hover .main-card__underline {
		border-top: 2px solid #fff;
	}

	.main-card__descr {
		margin: 0;
		margin-top: 15px;
		color: #fff;
		font-size: 14px;
	}
</style>
