<template v-for="(title, text) in articles">
	<section id="articles" >
		<h1 class="articlesheader">Artykuły opisujące szczegółowo sytuację z zanieczyszczeniem na świecie</h1>
		<div class="articles">
			<div class="article">
				<div class="artheader">
					<h1>{{  articles.articleone.title  }}</h1>
				</div>
					<div class="artcont">
					<p>
						{{  articles.articleone.text  }}
					</p>
				</div>
				<a href="#" class="artfull">

				</a>
			</div>

			<div class="article">
				<div class="artheader">
					<h1>{{  articles.articletwo.title  }}</h1>
				</div>
				<div class="artcont">
					<p>
						{{  articles.articletwo.text  }}
					</p>
				</div>
				<a href="#" class="artfull">

				</a>
			</div>

			<div class="article">
				<div class="artheader">
					<h1>{{  articles.articlethree.title  }}</h1>
				</div>

				<div class="artcont">
					<p>
						{{  articles.articlethree.text  }}
					</p>
				</div>
				<a href="#" class="artfull">

				</a>
			</div>
			<div class="article">
				<div class="artheader">
					<h1>{{  articles.articlethree.title  }}</h1>
				</div>

				<div class="artcont">
					<p>
						{{  articles.articlethree.text  }}
					</p>
				</div>
				<a href="#" class="artfull">

				</a>
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

$mobile: 767px;
$tablet: 1030px;

#articles {
	display: flex;
	flex-direction: column;
	align-items: center;
}

.articlesheader {
	text-align: center;
	color: $dark-green;
	font-size: 3vw;
	width: 70vw;
	margin-bottom: 7vw;
}

.articles {
	display: flex;
	flex-wrap: wrap;
	flex-direction: row;
	justify-content: space-evenly;
	padding: 4em 0em 0em 0em;
}

.article {
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 10vw;
	height: 18vw;
	width: 30vw;
	border-radius: 4vw 4vw 4vw 4vw;
	background: $green;

	.artheader {
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 0;
		padding: 0;
		height: 4vw;
		width: 80%;
		border-radius: 5em 5em 5em 5em;
		transform: translateY(-50%);
		background: $light-green;

		h1 {
			text-align: center;
			padding: 1vw;
			font-size: 2vw;
			color: $dark-green;
		}
	}

	.artcont {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 30vw;
		padding-bottom: 25%;
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
		position: absolute;
		height: 8vw;
		width: 8vw;
		border-radius: 100%;
		background: $dark-green;
		transform:translateY(175%)
	}
}

@media screen and (max-width: $tablet)
{

.articlesheader {
	text-align: center;
	color: $dark-green;
	font-size: 4vw;
	width: 80vw;
	margin-bottom: 7vw;
}

.article {
	margin-bottom: 20vw;
	height: 40vw;
	width: 60vw;
	border-radius: 6vw 6vw 6vw 6vw;

	.artheader {
		height: 7.5vw;

		h1 {
			padding: 1vw;
			font-size: 4.2vw;
		}
	}

	.artcont {
		width: 60vw;
		padding-bottom: 25%;
		p {
			font-size: 2.5vw;
			width: 80%;
		}
	}
	.artfull {
		position: absolute;
		height: 17.5vw;
		width: 17.5vw;
		border-radius: 100%;
		background: $dark-green;
		transform: translateY(180%);
	}
}
}

@media screen and (max-width: $mobile)
{

.articlesheader {
	text-align: center;
	color: $dark-green;
	font-size: 4.5vw;
	width: 90vw;
	margin-bottom: 7vw;
}

.article {
	margin-bottom: 20vw;
	height: 60vw;
	width: 80vw;

	.artheader {
		height: 10vw;

		h1 {
			padding: 1vw;
			font-size: 5.5vw;
		}
	}

	.artcont {
		width: 80vw;
		padding-bottom: 25%;
		p {
			font-size: 3.5vw;
			width: 80%;
		}
	}
	.artfull {
		position: absolute;
		height: 25vw;
		width: 25vw;
		border-radius: 100%;
		background: $dark-green;
		transform: translateY(190%);
	}
}
}
</style>