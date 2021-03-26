<template>
	<section id="hero">
		<div class='banner'>
			<img class='circle' src='@/assets/images/greenCircle.svg'>
			<img class='circle' src='@/assets/images/greenCircle.svg'>
			<img class='circle' src='@/assets/images/greenCircle.svg'>
			<header>
				<h1>Zostań z <span class='wordFocus'>nami</span> BardziejEKO</h1>
				<img class='pageLogo' src='@/assets/images/pageLogo.svg'>
			</header>
		</div>
		<article class='introduction'>
			<h2>Czemu uważamy, że to takie ważne?</h2>
			<div class='card'>
				<div class='background'>
					<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur id vestibulum libero. Nullam quis cursus mauris, sit amet imperdiet enim. Nam at urna sed urna blandit imperdiet. Donec non ante dapibus, commodo tellus et, scelerisque neque. Phasellus lorem turpis, tincidunt quis suscipit eu, viverra vitae tortor. Praesent vehicula feugiat tellus eu hendrerit.</p>
				</div>
				<img class='planet' src='@/assets/images/planet.svg'>
			</div>
		</article>
	</section>
</template>

<script>
export default {
	name: 'Hero',
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
$circle-size: 10vw;
$planet-size: 250px;

#hero {
	overflow-x: hidden;

	.banner {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 75vh;

		// smartphones only
		@media (max-width: $mobile) {
			height: 50vh;
		}

		// tablets only
		@media (max-width: $tablet) {
			height: 70vh;
		}

		header {
			display: flex;
			align-items: center;

			// smartphones only
			@media (max-width: $tablet) {
				flex-direction: column;
			}

			h1 {
				font-size: 4em;
				color: rgb(39, 22, 0);
				margin-right: 0.25em;

				// mobiles
				@media (max-width: $tablet) {
					font-size: 10vw;
					text-align: center;
					margin-right: 0;
					margin-bottom: 0.5em;
				}

				// smartphones only
				@media (max-width: $mobile) {
					font-size: 13vw;
				}

				.wordFocus {
					color: $green;
				}
			}

			.pageLogo {
				width: 10em;

				// smartphones only
				@media (max-width: $mobile) {
					width: 25vw;
				}

				// tablet only
				@media (max-width: $tablet) {
					width: 20vw;
				}
			}
		}

		.circle {
			position: absolute;
			transform: translate(50%, -50%);

			$ratio: 1;

			// mobiles
			@media (max-width: $tablet) {
				$ratio: 1.3;
				transform: translate(50%, -50%);
			}

			&:nth-child(1) {
				height: $circle-size * $ratio;
				top: 15%;
				left: 5%;

				// mobiles
				@media (max-width: $tablet) {
					top: 55%;
					left: -15%;
				}
			}

			&:nth-child(2) {
				height: $circle-size * .75 * $ratio;
				top: 80%;
				left: 65%;

				// mobiles
				@media (max-width: $tablet) {
					top: 85%;
					left: 89%
				}
			}

			&:nth-child(3) {
				height: $circle-size * 1.5 * $ratio;
				top: 2%;
				right: 5%;

				// mobiles
				@media (max-width: $tablet) {
					left: 50%
				}
			}
		}
	}

	.introduction {


		h2 {
			width: 55vw;
			color: $dark-green;
			padding: 1em 1.5em;
			font-size: 2.5em;
			letter-spacing: 2px;

			// mobiles
			@media (max-width: $tablet) {
				width: 100vw;
				padding: .5em 1.5em 1em 1.5em;
				font-size: 8vw;
				letter-spacing: 0;
				text-align: center;
			}
		}

		.card {
			display: flex;
			align-items: center;

			// mobiles
			@media (max-width: $tablet) {
				flex-direction: column;
			}

			.background {
				background: $green;
				width: 50vw;
				padding: 3em ($planet-size / 2) 3em 3em;
				border-radius: 0 50px 50px 0;

				// mobiles
				@media (max-width: $tablet) {
					width: 100%;
					padding: 4em 3em ($planet-size / 1.5) 3em;
					border-radius: 50px;
				}

				// smartphones only
				@media (max-width: $mobile) {
					padding: 3em 2em ($planet-size / 1.5) 2em;
				}

				p {
					color: $yellow;
					text-align: justify;
					font-size: 1.5em;
					font-weight: 500;
					letter-spacing: 1px;
					line-height: 32px;
				}

				// <p> tablets only
				@media (max-width: $tablet) {
					p {
						text-align: center;
						font-size: 3em;
						letter-spacing: 2px;
						line-height: 55px;
					}
				}

				// <p> smartphones only
				@media (max-width: $mobile) {
					p {
						text-align: center;
						font-size: 1.5em;
						letter-spacing: 1px;
						line-height: 27px;
					}
				}
			}

			.planet {
				display: block;
				position: relative;
				left: -110px;
				transform: rotate(-12deg);
				height: $planet-size;

				// mobiles
				@media (max-width: $tablet) {
					left: 0;
					top: -125px;
				}
			}
		}
	}
}
</style>