<template>
	<ul v-if="aComments.length" class="comment">
		<li
			v-for="(oComment, index) in aComments"
			:key="'comment' + index"
			class="comment__item"
		>
			<div class="comment__item__author-image">
				<img :src="oComment.author.image" width="55" height="55" alt="demo" />
			</div>

			<div class="comment__item__cta cta__btn">
				<button class="cta__btn__item cta__btn__item--share">{{ oComment.cta.share }}</button>
				<button class="cta__btn__item cta__btn__item--like">{{ oComment.cta.like }}</button>
			</div>

			<span>post by</span>

			<div>
				<span class="comment__item__author-name">{{ oComment.author.name }}</span>
				<span class="comment__item__reply">reply</span>
			</div>

			<div class="comment__item__date">{{ oComment.date }}</div>

			<div class="comment__item__content">
				<template v-if="oComment.aAttachment">
					<p v-for="(attachment, index) in oComment.aAttachment" :key="'attachment' + index">
						<img :src="attachment" alt="demo" />
					</p>
				</template>

				<p v-html='oComment.content'></p>
			</div>

			<template v-if="oComment.aAnswers">
				<ul class="comment">
					<li
						v-for="(oAnswer, index) in oComment.aAnswers"
						:key="'oAnswer' + index"
						class="comment__item"
					>
						<div class="comment__item__author-image">
							<img :src="oAnswer.author.image" width="55" height="55" alt="demo" />
						</div>

						<div class="comment__item__cta cta__btn">
							<button class="cta__btn__item cta__btn__item--share">{{ oAnswer.cta.share }}</button>
							<button class="cta__btn__item cta__btn__item--like">{{ oAnswer.cta.like }}</button>
						</div>

						<span>post by</span>

						<div>
							<span class="comment__item__author-name">{{ oAnswer.author.name }}</span>
							<span class="comment__item__reply">reply</span>
						</div>

						<div class="comment__item__date">{{ oAnswer.date }}</div>

						<div class="comment__item__content">
							<template v-if="oAnswer.attachment">
								<p v-for="(attachment, index) in oAnswer.attachment">
									<img :src="attachment" alt="demo" />
								</p>
							</template>

							<p v-html="oAnswer.content"></p>
						</div>
					</li>
				</ul>

				<div class="more-comments">24 more comments</div>
			</template>
		</li>
	</ul>
</template>

<script>
export default {
	name: "comment-list",

	props: {
		aComments: {
			type: Array,
			default: []
		}
	}
};
</script>

<style lang="scss">
.comments
{
	max-width: 840px;
	margin-left: auto;
	margin-right: auto;
	padding: 15px 50px 55px;
	background-color: #fff;
	box-shadow: 0px 0px 13px 0px rgba(0, 0, 0, 0.15);
	font-family: 'Josefin Sans', sans-serif;

	&__title
	{
		margin-bottom: 15px;
		line-height: 1.2;
		font-size: 24px;
		color: #000;
	}
}

.comment
{
	margin: 0;
	padding: 0;
	list-style: none;
	border-bottom: 2px solid rgba(#555, 0.2);

	.comment { border-bottom: none; }

	&__item
	{
		border-top: 2px solid rgba(#555, 0.2);
		margin-top: 20px;
		padding-top: 20px;
		padding-left: 80px;
		line-height: 1;
		color: #000;

		&:first-child
		{
			margin-top: 0;
		}

		&__author-image
		{
			margin-left: -80px;
			float: left;
		}

		&__cta
		{
			float: right;
		}

		&__author-name
		{
			line-height: 1.6;
			font-weight: 700;
		}

		&__reply
		{
			margin-left: 10px;
			font-size: 12px;
			font-weight: 700;
			text-decoration: underline;
			color: #629494;
			cursor: pointer;

			&:hover,
			&:focus
			{
				text-decoration: none;
			}
		}

		&__date
		{
			margin-bottom: 10px;
			font-size: 12px;
			font-weight: 700;
			color: #629494;
		}

		&__content
		{
			margin-bottom: 15px;
			line-height: 1.4;
			font-weight: 300;

			p
			{
				&:last-child
				{
					margin-bottom: 0;
				}
			}

			strong
			{
				font-weight: 700;
			}
		}
	}

	.more-comments
	{
		margin-bottom: 20px;
		font-size: 16px;
		text-align: center;
		color: rgba(#000, 0.54);
		cursor: pointer;
	}
}

.cta__btn
{
	font-size: 0;

	&__item
	{
		display: inline-block;
		vertical-align: middle;
		margin-left: 15px;
		padding: 0;
		border: none;
		background: transparent;
		box-shadow: none;
		outline: none;
		font-size: 12px;
		font-weight: 700;

		&:after
		{
			content: '';
			display: inline-block;
			vertical-align: top;
			width: 10px;
			height: 10px;
			margin-left: 5px;
			background-repeat: no-repeat;
		}

		&:first-child
		{
			margin-left: 0;
		}

		&--share
		{
			&:after
			{
				background-image: url(../assets/share-alt.svg);
			}
		}

		&--like
		{
			&:after
			{
				background-image: url(../assets/thumbs-up.svg);
			}
		}
	}
}
</style>
