<template>
	<div class="pricing__item pricing__item--shadow">
		<div class="pricing__item__header">
			<h4 class="pricing__item__title">{{ oPrice.title }}</h4>

			<div class="pricing__item__price">
				<sup>$</sup>{{ oPrice.price }}<sub>per month</sub>
			</div>
		</div>

		<div class="pricing__item__body">
			<ul v-if="oPrice.aDescriptions"
				class="pricing__item__description"
			>
				<li v-for="(description, index) in oPrice.aDescriptions" :key="'description' + index">
					{{ description }}
				</li>
			</ul>
		</div>

		<div class="pricing__item__footer">
			<button
				@click="onOrder(oPrice.title)"
				type="button"
				class="pricing__item__btn"
			>
				Order Now
			</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "pricing-item",

	props: {
		oPrice: {
			type: Object,
			default: {}
		}
	},

	methods: {
		onOrder (_sMessage)
		{
			alert('Your choice ' + _sMessage)
		}
	}
};
</script>

<style lang="scss">
.pricing__item
{
	position: relative;
	width: 100%;
	margin-bottom: 30px;
	background-color: #fff;
	padding: 45px 15px 65px;
	line-height: 1.4;
	font-size: 17px;
	font-family: 'Open Sans', sans-serif;
	text-align: center;
	overflow: hidden;
	transition: box-shadow .35s ease-in-out;

	&:before
	{
		content: "";
		display: block;
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 210px;
		background-color: #3949ab;
		transform: skewY(-4deg);
		transform-origin: top left;
	}

	@media (min-width: 576px)
	{
		display: flex;
		flex-direction: column;
		align-items: center;

		&__header { flex: 0 0 auto; }

		&__body { flex: 1 0 auto; }

		&__footer { flex: 0 0 auto; }
	}

	> div
	{
		position: relative;
		width: 100%;
		z-index: 1;
	}

	&__title,
	&__price
	{
		color: #fff;
	}

	&__title
	{
		margin-bottom: 30px;
		line-height: 1.2;
		font-size: 25px;
		font-weight: 400;
		letter-spacing: 0.05em;
	}

	&__price
	{
		line-height: 0.8;
		font-size: 50px;
		letter-spacing: 0.05em;

		sup
		{
			vertical-align: middle;
			font-size: 25px;
		}

		sub
		{
			bottom: auto;
			font-size: 17px;
		letter-spacing: 0.03em;
		}
	}

	&__description
	{
		max-width: 180px;
		margin: 100px auto 65px;
		padding: 0;
		line-height: 1.4;
		font-weight: 300;
		list-style: none;

		li
		{
			margin-top: 20px;
			padding-top: 10px;
			padding-bottom: 10px;
			border-bottom: 1px solid #bfbfbf;

			&:first-child { margin-top: 0; }
		}
	}

	&__btn
	{
		display: inline-block;
		vertical-align: middle;
		min-width: 180px;
		padding: 15px 10px;
		line-height: 1.3;
		font-size: 20px;
		font-weight: 600;
		color: #212121;
		border: 2px solid #000;
		background-color: transparent;
		text-align: center;
		text-decoration: none !important;
		text-shadow: none;
		text-transform: uppercase;
		letter-spacing: 0;
		box-shadow: none;
		outline: none !important;
		cursor: pointer;
		user-select: none;
		-webkit-user-drag: none;
		user-drag: none;
		-ms-touch-action: manipulation;
		touch-action: manipulation;
		transition: background-color .25s ease-in-out,border-color .25s ease-in-out,color .25s ease-in-out;

		&:hover,
		&:focus
		{
			background-color: #00897b;
			border-color: #00897b;
			color: #fff;
		}
	}

	&--shadow
	{
		&:hover
		{
			box-shadow: 0px 3px 25px 0px rgba(0, 0, 0, 0.35);
		}
	}
}
</style>
