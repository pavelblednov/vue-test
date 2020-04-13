<template>
	<div>
		<section class="section section--pricing">
			<div class="container">
				<pricing-list :aPrices="aPrices" />
			</div>
		</section>

		<section class="section section--review">
			<div class="container">
				<div class="row justify-content-center">
					<div class="col-12 col-lg-10">
						<review-list :aReview="aReview" />
					</div>
				</div>
			</div>
		</section>

		<section class="section section--comment">
			<div class="container">
				<div class="comments">
					<div class="comments__title">Comments</div>

					<comment-list :aComments="aComments" />
				</div>
			</div>
		</section>
	</div>
</template>

<script>
import PricingList from '@/components/PricingList.vue';
import ReviewList from '@/components/ReviewList.vue';
import CommentList from '@/components/CommentList.vue';

export default {
	name: 'Home',

	components: {
		'pricing-list': PricingList,
		'review-list': ReviewList,
		'comment-list': CommentList
	},

	data: function ()
	{
		return {
			aPrices: [
				{
					title: 'Free Trail',
					price: '00',
					aDescriptions: ['30 Free Trail', '5 Free Projects', 'PHP 5 Enabled', '24/7 Suports']
				},
				{
					title: 'Basic',
					price: '50',
					aDescriptions: ['30 Free Trail', '5 Free Projects', 'PHP 5 Enabled', '24/7 Suports']
				},
				{
					title: 'Ultimates',
					price: '99',
					aDescriptions: ['30 Free Trail', '5 Free Projects', 'PHP 5 Enabled', '24/7 Suports']
				}
			],
			aReview: [
				{
					img: require('@/assets/ava.jpg'),
					name: 'Limara tusi',
					position: 'CEO, RanDOM COMPANY',
					text: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec'
				},
				{
					img: require('@/assets/ava.jpg'),
					name: 'Ann MIller',
					position: 'UI/UX Designer',
					text: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec'
				},
				{
					img: require('@/assets/ava.jpg'),
					name: 'Chloe Carter',
					position: 'Programmer',
					text: 'Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec'
				}
			],
			aComments: [
				{
					author: {
						image: require('@/assets/ava_comment.png'),
						name: 'Smuckersreg Toppings',
					},
					cta: {
						share: 456,
						like: 15
					},
					date: '6/10/2014',
					aAttachment: [require('@/assets/recipe.jpg')],
					content: 'Thanks for the recipe',

					aAnswers: [
						{
							author: {
								image: require('@/assets/ava_comment.png'),
								name: 'Ann MIller',
							},
							cta: {
								share: 56,
								like: 155
							},
							date: '16/9/2016',
							content: '<strong>Thanks for the recipe lorem ipsum bla bla bla  Thanks for the recipe lore</strong>'
						}
					]
				},
				{
					author: {
						image: require('@/assets/ava_comment.png'),
						name: 'Chloe Carter',
					},
					cta: {
						share: 123,
						like: 255
					},
					date: '16/9/2016',
					content: 'Thanks for the recipe'
				}
			]
		};
	}
}
</script>

<style lang="scss">
	.section
	{
		position: relative;
		padding-top: 125px;
		padding-bottom: 125px;

		&--pricing { background-color: #f0f1f1; }
		&--review { }
		&--comment { background-color: #eaeaea; }
	}
</style>
