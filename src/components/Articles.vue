<template v-for="(title, text) in articles">
	<section id="articles" >
		<div class="articlesleft">
			<div class="articleleft">
				<div class="artheader">
					<h1>{{  articles.articleone.title  }}</h1>
				</div>
				<div class="artmiddle">
					<div class="artcont">
						<p>
							{{  articles.articleone.text  }}
						</p>
					</div>
					<a href="#" class="artfull">

					</a>
				</div>
			</div>

			<div class="articleleft">
				<div class="artheader">
					<h1>{{  articles.articletwo.title  }}</h1>
				</div>
				<div class="artmiddle">
					<div class="artcont">
						<p>
							{{  articles.articletwo.text  }}
						</p>
					</div>
					<a href="#" class="artfull">

					</a>
				</div>
			</div>
		</div>

		<div class="articlesright">
			<div class="articleright">
				<div class="artheader">
					<h1>{{  articles.articlethree.title  }}</h1>
				</div>
				<div class="artmiddle">
					<a href="#" class="artfull">

					</a>
					<div class="artcont">
						<p>
							{{  articles.articlethree.text  }}
						</p>
					</div>
				</div>
			</div>

			<div class="articleright">
				<div class="artheader">
					<h1>{{  articles.articlefour.title  }}</h1>
				</div>
				<div class="artmiddle">
					<a href="#" class="artfull">

					</a>
					<div class="artcont">
						<p>
							{{  articles.articlefour.text  }}
						</p>
					</div>
				</div>
			</div>
		</div>

	</section>
</template>

<script>
export default {
	name: 'Articles',
	data() {
		return {
			articles: {
				articleone: {
					title: "Article's Title",
					text: `	Lorem ipsum dolor sit, amet consectetur adipisicing elit.
							Tempore est tenetur in accusamus, doloribus alias eius
							consectetur molestias, sint perferendis numquam perspiciatis
							tempora non odio. Ipsum excepturi quis enim culpa?`,
				},
				articletwo: {
					title: "Second Article's Title",
					text: `	Second Lorem ipsum dolor sit, amet consectetur adipisicing elit.
							Tempore est tenetur in accusamus, doloribus alias eius
							consectetur molestias, sint perferendis numquam perspiciatis
							tempora non odio. Ipsum excepturi quis enim culpa?`,
				},
				articlethree: {
					title: "Third Article's Title",
					text: `	Third Lorem ipsum dolor sit, amet consectetur adipisicing elit.
							Tempore est tenetur in accusamus, doloribus alias eius
							consectetur molestias, sint perferendis numquam perspiciatis
							tempora non odio. Ipsum excepturi quis enim culpa?`,
				},
				articlefour: {
					title: "Fourth Article's Title",
					text: `	Fourth Lorem ipsum dolor sit, amet consectetur adipisicing elit.
							Tempore est tenetur in accusamus, doloribus alias eius
							consectetur molestias, sint perferendis numquam perspiciatis
							tempora non odio. Ipsum excepturi quis enim culpa?`,
				},
			}
		}
	},
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/properties';
// $yellow;
// $light-green;
// $green;
// $dark-green;

// $padding-main;

#articles {
	display: flex;
	flex-direction: row;
	justify-content: space-between;
	padding: 4em 0em 1em 0em;
	background: pink;
}

.articlesleft {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	height: 35vw;
}

.articleleft {
	display: block;
	flex-direction: column;
	justify-content: center;
	height: 15vw;
	width: 35vw;
	border-radius: 0px 4vw 4vw 0px;
	background: $green;

	.artheader {
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 0;
		padding: 0;
		height: 4vw;
		width: 80%;
		border-radius: 0em 5em 5em 0em;
		transform: translateY(-50%);
		background: $light-green;

		h1 {
			padding: 1vw;
			font-size: 2.2vw;
			color: $dark-green;
			transform: translateX(8%);
		}
	}

	.artmiddle {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		margin: 0;
		padding: 0;
		width: 39vw;
		height: 15vw;
		transform: translateY(-25%);
	}

	.artcont {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 30vw;
		p {
			padding: 0em 0em 0em 0em;
			font-weight: 500;
			font-size: 1.15vw;
			text-align: center;
			letter-spacing: 0.06em;
			color: $yellow;
			width: 80%;
		}
	}
	.artfull {
		height: 8vw;
		width: 8vw;
		border-radius: 100%;
		background: $dark-green;
	}
}

.articlesright {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	height: 35vw;
}

.articleright {
	display: flex;
	flex-direction: column;
	justify-content: center;
	height: 15vw;
	width: 35vw;
	border-radius: 4vw 0vw 0vw 4vw;
	background: $green;

	.artheader {
		display: flex;
		justify-content: flex-start;
		align-items: center;
		align-self: flex-end;
		margin: 0;
		padding: 0;
		height: 4vw;
		width: 80%;
		border-radius: 5em 0em 0em 5em;
		transform: translateY(-50%);
		background: $light-green;

		h1 {
			padding: 1vw;
			font-size: 2.2vw;
			color: $dark-green;
			transform: translateX(8%);
		}
	}

	.artmiddle {
		display: flex;
		flex-direction: row;
		align-items: center;
		align-self: flex-end;
		margin: 0;
		padding: 0;
		width: 39vw;
		height: 15vw;
		transform: translateY(-15%);
	}

	.artcont {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 30vw;
		p {
			padding: 0em 0em 0em 0em;
			font-weight: 500;
			font-size: 1.15vw;
			text-align: center;
			letter-spacing: 0.06em;
			color: $yellow;
			width: 80%;
		}
	}
	.artfull {
		height: 8vw;
		width: 8vw;
		border-radius: 100%;
		background: $dark-green;
	}
}
</style>