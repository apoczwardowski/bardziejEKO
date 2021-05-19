<template>
	<section id="charity">
		<div class="header">
			<div class="charityheader">
				<h2>$</h2>
				<h1>Tu możesz złożyć dotację na wybraną zbiórkę</h1>
			</div>
		</div>

		<div class="charities">
			<div class="charitiesleft">

				<div class="charity" v-for="(charity, index) in charities" :key="index">

					<div class="charitycircle" v-if="(index % 2 == 0)">
						<img :src="charity.image" alt="background" class="backgroundimg">
						<a href=""><img src="@/assets/images/arrow.svg" alt="arrow" class="arrow"><p class="link">Przejdź</p></a>
					</div>

					<div class="charitytitle" v-if="(index % 2 == 0)">
						<p>{{  charity.title  }}</p>
					</div>

				</div>

			</div>

			<div class="charitiesright">

				<div class="charity" v-for="(charity, index) in charities" :key="index">

					<div class="charitytitle" v-if="(index % 2 != 0)">
						<p>{{  charity.title  }}</p>
					</div>

					<div class="charitycircle" v-if="(index % 2 != 0)">
						<img :src="charity.image" alt="background" class="backgroundimg">
						<a href=""><img src="@/assets/images/arrow.svg" alt="arrow" class="arrow"><p class="link">Przejdź</p></a>
					</div>

				</div>

			</div>
		</div>
	</section>
</template>

<script>
export default {
	name: 'Charity',
		data() {
			return {
				charities: [
					{
						image: require(`../assets/images/smoke.png`),
						title: "Zbiórka na walkę z emisją dwutlenku węgla 1",
					},
					{
						image: require(`../assets/images/smoke.png`),
						title: "Zbiórka na walkę z emisją dwutlenku węgla 2",
					},
					{
						image: require(`../assets/images/smoke.png`),
						title: "Zbiórka na walkę z emisją dwutlenku węgla 3",
					},
					{
						image: require(`../assets/images/smoke.png`),
						title: "Zbiórka na walkę z emisją dwutlenku węgla 4",
					},
				]
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

#charity {
	//padding: $padding-main;
}

.header {
	display: flex;
	justify-content: flex-end;
}

.charityheader {
	display: flex;
	justify-content: space-evenly;
	align-items: center;
	background: $green;
	margin-right: 6em;
	width: 50vw;
	border-radius: 2.5vw;
	h1 {
		font-size: 2.5vw;
		padding: 2vw 10vw 2vw 10vw;
		color: $yellow;
	}
	h2 {
		position: absolute;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 6vw;
		height: 6vw;
		left: 44vw;
		font-size: 3vw;
		background: $light-green;
		color: $dark-green;
		border-radius: 100vw;
		transform: translateY(100%);
	}
}

.charities {
	display: flex;
	flex-direction: row;
	align-items: center;
	justify-content: space-evenly;
	width: 100vw;
	height: 68vw;
}

.charitiesleft {
	display: flex;
	flex-direction: column;
	justify-content: space-evenly;
	align-items: center;
	//height: 60vw;

	.charity {
		display: flex;
		flex-direction: row;
		align-items: center;
		width: 46vw;
		margin-bottom: 5vw;
		transform: scale(.80);

		.charitycircle {
			display: flex;
			justify-content: center;
			align-items: center;
			background: $dark-green;
			width: 16vw;
			height: 16vw;
			border-radius: 100vw;
			z-index: 100;
			transform:translateX(35%);

			a {
				position:absolute;
				display: flex;
				justify-content: center;
				align-items: center;

				.arrow{
					width: 8vw;
					transform: translate(15%, 2%);
				}
				.link {
					position: absolute;
					font-size: 1.2vw;
					padding-left: .3em;
					color: $dark-green;
					transform: translateY(5%);
					font-weight: 700;
					letter-spacing: .6px;
				}
			}
			.backgroundimg {
				width: 14.5vw;
			}
		}

		.charitytitle {
			display: flex;
			justify-content: center;
			align-items: center;
			background: $light-green;
			color: $dark-green;
			width: 30vw;
			height: 13vw;
			padding-left: 7vw;
			font-size: 2.5vw;
			font-weight: 500;
			z-index: 10;
			border-end-end-radius: 4vw;
			border-start-end-radius: 4vw;
		}
	}
}
.charitiesright {
	display: flex;
	flex-direction: column;
	justify-content: space-evenly;
	align-items: center;
	//height: 60vw;
	margin-top: 6vw;

	.charity {
		display: flex;
		flex-direction: row;
		align-items: center;
		margin-top: 5vw;
		transform: scale(.80);

		.charitycircle {
			display: flex;
			justify-content: center;
			align-items: center;
			background: $dark-green;
			width: 16vw;
			height: 16vw;
			border-radius: 100vw;
			z-index: 100;
			transform:translateX(-35%);

			a {
				position:absolute;
				display: flex;
				justify-content: center;
				align-items: center;

				.arrow{
					width: 8vw;
					transform: translate(15%, 2%);
				}

				.link {
					position: absolute;
					font-size: 1.2vw;
					padding-left: .3em;
					color: $dark-green;
					transform: translateY(5%);
					font-weight: 700;
					letter-spacing: .6px;
				}
			}
			.backgroundimg {
				width: 14.5vw;
			}
		}

		.charitytitle {
			display: flex;
			justify-content: center;
			align-items: center;
			background: $light-green;
			color: $dark-green;
			width: 30vw;
			height: 13vw;
			font-weight: 500;
			padding-right: 7vw;
			padding-left: 2vw;
			font-size: 2.5vw;
			z-index: 10;
			border-end-start-radius: 4vw;
			border-start-start-radius: 4vw;
		}
	}
}

@media screen and (max-width: $tablet) {
	.header {
		justify-content: center;
	}
	.charityheader{
		margin-right: 0em;
		width: 70vw;
		text-align: center;
		h1 {
			font-size: 4.5vw;
			padding: 2vw 4vw 2vw 4vw;
		}
		h2 {
			width: 10vw;
			height: 10vw;
			left: 46vw;
			font-size: 6.5vw;
			transform: translateY(110%);
		}
	}

	.charities {
		height: 90vw;
	}

	.charitiesleft {
		transform: translate(15%, 7%);
		.charity {
			margin-bottom: 10vw;
			@supports (-moz-appearance:none) {
				transform: scale(1.2);
			}
			transform: scale(1.2);
		}
	}
	.charitiesright {
		transform: translateX(-15%);
		.charity {
			margin-top: 10vw;
			@supports (-moz-appearance:none) {
				transform: scale(1.2);
			}
			transform: scale(1.2);
		}
	}
}

@media screen and (max-width: $mobile) {
	.header {
		justify-content: center;
	}
	.charityheader{
		width: 85vw;
		text-align: center;
		h1 {
			font-size: 6.5vw;
			padding: 2vw 2vw 4vw 2vw;
		}
		h2 {
			width: 15vw;
			height: 15vw;
			left: 44.5vw;
			font-size: 8.5vw;
			transform: translateY(105%);
		}
	}

	.charities {
		height: 170vw;
		transform:translateY(-5%);
	}

	.charitiesleft {
		transform: translate(40%, 15%);
		.charity {
			margin-bottom: 25vw;
			@supports (-moz-appearance:none) {
				transform: scale(1.6);
			}
			transform: scale(1.8);
		}
	}
	.charitiesright {
		transform: translateX(-40%);
		.charity {
			margin-top: 25vw;
			@supports (-moz-appearance:none) {
				transform: scale(1.6);
			}
			transform: scale(1.8);
		}
	}
}
</style>