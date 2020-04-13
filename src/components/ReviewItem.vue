<template functional>
	<div
		class="review__item"
		:class="[data.staticClass, data.class]"
	>
		<div class="d-table">
			<div class="d-table-cell align-top">
				<div class="review__item__author-image">
					<img :src="props.oReview.img" alt="demo" />
				</div>
			</div>

			<div class="d-table-cell align-top">
				<div class="review__item__content">
					<span class="review__item__author-name">{{ props.oReview.name }}</span>
					<span class="review__item__author-position">{{ props.oReview.position }}</span>
					<p>{{ props.oReview.text }}</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "review-item",

	props: {
		oReview: {
			type: Object,
			default: {}
		}
	}
};
</script>

<style lang="scss">
.review__item
{
	margin-left: 120px;
	margin-right: 65px;

	&__content
	{
		font-size: 16px;
		text-transform: uppercase;

		p
		{
			line-height: 1.6;
			color: rgba(#212121, 0.6);
		}
	}

	&__author-image
	{
		margin-right: 30px;
	}

	&__author-name,
	&__author-position
	{
		display: block;
	}

	&__author-name
	{
		font-size: 30px;
		font-weight: 700;
	}

	&__author-position
	{
		margin-bottom: 10px;
		line-height: 1;
		font-size: 12px;
		font-style: italic;
	}
}
</style>
