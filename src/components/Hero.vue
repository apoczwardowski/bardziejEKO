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
			<div class='background'>
				<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur id vestibulum libero. Nullam quis cursus mauris, sit amet imperdiet enim. Nam at urna sed urna blandit imperdiet. Donec non ante dapibus, commodo tellus et, scelerisque neque. Phasellus lorem turpis, tincidunt quis suscipit eu, viverra vitae tortor. Praesent vehicula feugiat tellus eu hendrerit. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur id vestibulum libero. Nullam quis cursus mauris, sit amet imperdiet enim. Nam at urna sed urna blandit imperdiet. Phasellus lorem turpis, tincidunt quis suscipit eu. Lorem ipsum dolor sit amet.</p>
			</div>
			<div class='icon-background'>
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

// breakpoints
$tablets: 1200px;
$smartphones: 760px;

#hero {
	overflow-x: hidden;

	.banner {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		height: 50vh;

		// tablets
		@media (max-width: $tablets) {
			height: 25vh;
		}

		// smartphones
		@media (max-width: $smartphones) {
			height: 45vh;
		}

		header {
			display: flex;
			align-items: center;

			// smartphones
			@media (max-width: $smartphones) {
				flex-direction: column;
			}

			h1 {
				font-size: 4em;
				color: rgb(39, 22, 0);
				margin-right: 0.25em;

				// tablets
				@media (max-width: $tablets) {
					font-size: 5vw;
				}

				// smartphones
				@media (max-width: $smartphones) {
					font-size: 10vw;
					text-align: center;
				}

				.wordFocus {
					color: $green;
				}
			}

			.pageLogo {
				width: 10em;

				// tablets
				@media (max-width: $tablets) {
					width: 6em;
				}

				// smartphones
				@media (max-width: $smartphones) {
					width: 30vw;
					margin-top: 1em;
				}
			}
		}

		.circle {
			position: absolute;
			transform: translate(50%, -50%);

			&:nth-child(1) {
				height: 8vw;
				top: 10%;
				left: 2%;

				// smartphones
				@media (max-width: $smartphones) {
					height: 20vw;
					top: 19%;
					left: -20%;
				}
			}

			&:nth-child(2) {
				height: 4vw;
				top: 80%;
				left: 80%;

				// tablets
				@media (max-width: $tablets) {
					height: 4vw;
					top: 90%;
					left: 85%;
				}

				// smartphones
				@media (max-width: $smartphones) {
					height: 10vw;
					top: 85%;
					left: 75%;
				}
			}

			&:nth-child(3) {
				height: 10vw;
				top: 2%;
				right: 5%;

				// smartphones
				@media (max-width: $smartphones) {
					height: 35vw;
					top: 2%;
					right: 1%;
				}
			}
		}
	}

	.introduction {
		margin-top: 5em;
		padding: 0 10vw;
		display: grid;
		grid-template-columns: 4fr 1fr;
		grid-template-areas:
		"title   ."
		"content icon";

		// tablets
		@media (max-width: $tablets) {
			margin-top: 4em;
			grid-template-columns: 1fr;
			grid-template-areas:
			"title"
			"content"
			"icon";
		}

		// smartphones
		@media (max-width: $smartphones) {
			padding: 0;
		}

		h2 {
			grid-area: title;
			margin-bottom: .5em;
			text-align: center;
			font-size: 2.5em;
			letter-spacing: 1px;
			color: $dark-green;

			// tablets
			@media (max-width: $tablets) {
				font-size: 4vw;
				letter-spacing: 0;
			}

			// smartphones
			@media (max-width: $smartphones) {
				font-size: 8vw;
			}
		}

		.background {
			grid-area: content;
			background: $green;
			border-radius: 35px;
			padding: 2.5em;

			p {
				color: $yellow;
				font-size: 1.5em;
				font-weight: 300;
				line-height: 30px;
				letter-spacing: 1px;

				// tablets
				@media (max-width: $tablets) {
					font-size: 3vw;
					text-align: justify;
					line-height: 3.75vw;
					letter-spacing: 1px;
				}

				// smartphones
				@media (max-width: $smartphones) {
					font-size: 6vw;
					text-align: center;
					line-height: 6.5vw;
					letter-spacing: 0;
					word-spacing: 3px;
				}
			}
		}

		.icon-background {
			grid-area: icon;
			background: $dark-green;
			margin: 2em 0;
			padding: 1.75em;
			border-radius: 0 35px 35px 0;
			display: flex;
			justify-content: center;
			align-items: center;

			// tablets
			@media (max-width: $tablets) {
				width: 30vw;
				height: 30vw;
				margin: 0;
				padding: 2em;
				border-radius: 0 0 35px 35px;
				position: relative;
				left: 50%;
				transform: translateX(-50%);
			}

			// smartphones
			@media (max-width: $smartphones) {
				padding: 1.25em;
			}


			.planet {
				width: 100%;
				transform: rotate(-15deg);

				// tablets
				@media (max-width: $tablets) {
					width: 90%;
				}

				// smartphones
				@media (max-width: $smartphones) {
					width: 100%;
				}
			}
		}
	}
}
</style>