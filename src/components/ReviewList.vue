<template>
	<div class="review" ref="glide">
		<div data-glide-el="track" class="glide__track">
			<div class="glide__slides">
				<div
					v-for="(oReview, index) in aReview"
					:key="'glide__slide' + index"
					class="glide__slide"
				>
					<review-item :oReview="oReview" />
				</div>
			</div>
		</div>

		<div class="glide__bullets" data-glide-el="controls[nav]">
			<button type="button" class="glide__bullet"
				v-for="index in aReview.length"
				:key="'glide__bullet' + index"
				:data-glide-dir="'=' + (index - 1)"
			></button>
		</div>
	</div>
</template>

<script>
import ReviewItem from '@/components/ReviewItem.vue';

import Glide from '@glidejs/glide';

export default {
	name: "review-list",

	components: {
		'review-item': ReviewItem
	},

	props: {
		aReview: {
			type: Array,
			default: []
		}
	},

	mounted ()
	{
		this.$nextTick(this.init);
	},

	beforeDestroy ()
	{
		this.destroy();
	},

	methods: {
		init ()
		{
			var option = {
				type: 'carousel',
				perView: 1,
				gap: 0,
				keyboard: false,
				swipeThreshold: 10,
				dragThreshold: 30,
				autoplay: 5000,
				animationDuration: 500,
				animationTimingFunc: 'cubic-bezier(0,0,0.2,1)'
			};

			var oSlider = this.slider = new Glide(this.$refs.glide, option);

			oSlider.mount();
		},

		destroy ()
		{
			if (this.slider && this.slider.destroy)
			{
				this.slider.destroy();
				this.slider = null;
			}
		}
	}
}
</script>

<style lang="scss">
@import "~@glidejs/glide/dist/css/glide.core.min.css";

.review
{
	position: relative;
	padding-top: 80px;
	padding-bottom: 105px;
	border: 1px solid #212121;
}

.glide
{
	&__bullets
	{
		position: absolute;
		z-index: 2;
		left: 0;
		bottom: 40px;
		width: 100%;
		font-size: 0;
		text-align: center;
	}

	&__bullet
	{
		background-color: #fff;
		width: 13px;
		height: 13px;
		padding: 0;
		border-radius: 0;
		border: 1px solid #212121;
		transition: all 300ms ease-in-out;
		cursor: pointer;
		line-height: 0;
		margin: 0 2px;

		&:focus
		{
			outline: none;
		}

		&:hover,
		&:focus
		{
			background-color: rgba(#212121, 0.8);
		}

		&--active
		{
			background-color: #212121;
		}
	}

	&--swipeable
	{
		cursor: grab;
		cursor: -moz-grab;
		cursor: -webkit-grab;
	}

	&--dragging
	{
		cursor: grabbing;
		cursor: -moz-grabbing;
		cursor: -webkit-grabbing;
	}
}
</style>
