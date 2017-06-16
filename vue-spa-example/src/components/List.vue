<!-- List.vue -->
<template>
	<li class="sec_li">
		<router-link :to="{ name: 'detail', params: { id: price }}" class="lp_li_a">
			<div class="lp_li_imgWrap">
				<img :src=" img ">
			</div>
			<p class="lp_li_name">{{ title }}</p>
			<p class="lp_li_price">￥{{ price }}元</p>
		</router-link>
	</li>
</template>

<style scoped>
	.sec_li {
		float: left;
		width: 50%;
		margin-bottom: 0.1rem;
		height: 290px;
	}
	.lp_li_a {
		display: block;
		padding: 0.3rem 0;
		margin: 0 0.05rem;
		text-align: center;
		background: #fff;
	}
	.lp_li_imgWrap {
		padding: 0.24rem 0;
	}
	.lp_li_imgWrap > img {
		width: auto;
		height: 8.3rem;
	}
	.lp_li_name {
		height: 0.5rem;
		line-height: 0.5rem;
		font-size: 16px;
		color: #333;
	}
	.lp_li_price {
		height: 0.5rem;
		line-height: 0.5rem;
		font-size: 16px;
		color: #fb3b3b;
	}
</style>

<script>
	export default {
		props: ['price', 'title', 'img']
	}
</script>