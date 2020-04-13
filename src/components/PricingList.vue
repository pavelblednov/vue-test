<template functional>
	<div
		class="pricing"
		:class="[data.staticClass, data.class]"
	>
		<div class="row">
			<div
				v-for="(oPrice, index) in props.aPrices"
				:key="oPrice.price + '-' + index"
				class="col-12 col-md-6 col-lg-4  d-sm-flex"
			>
				<component
					:is="props.components.PricingItem"
					:class="[data.staticClass, data.class]"
					:oPrice="oPrice"
				/>
			</div>
		</div>
	</div>
</template>

<script>
import PricingItem from '@/components/PricingItem.vue';

export default {
	name: "pricing-list",

	props: {
		components: {
			type: Object,
			default: function ()
			{
				return {
					PricingItem: PricingItem
				};
			}
		},
		aPrices: {
			type: Array,
			default: []
		}
	}
}
</script>

<style lang="scss">
.pricing
{
	margin-bottom: -30px;
}
</style>
