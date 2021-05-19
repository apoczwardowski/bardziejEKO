<template>
	<footer id="footer">
		<div class="image"></div>
		<section class="content">
			<div class="link">
				<a href="#">
					<div class="container">
						<img src="@/assets/images/fb.svg" alt="fanpage facebook">
						<div class="text">
							<p>/bardziejeko</p>
							<span>Zobacz nasz fanpage</span>
						</div>
					</div>
				</a>
			</div>
			<div class="link">
				<a href="#">
					<div class="container">
						<img src="@/assets/images/envelope.svg" alt="email kontaktowy">
						<div class="text">
							<p>kontakt@bardziejeko.edu.pl</p>
							<span>Skontaktuj się z nami</span>
						</div>
					</div>
				</a>
			</div>
			<p class="description">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nibh arcu eget vulputate ultricies sed nisl molestie lacus. Nisi pellentesque pulvinar sit nisl, augue nibh vel posuere quis. Dolor etiam laoreet ultrices quis fermentum. Quisque non ullamcorper amet posuere duis felis in.</p>
			<div class="zwolnieni-logo">
				<img src="@/assets/images/zwzt.svg" alt="Zwolnieni Z Teorii">
			</div>
			<div class="copyright">
				<span>&copy; BardziejEKO 2021</span>
			</div>
		</section>
	</footer>
</template>

<script>
export default {
	name: 'Footer',
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

#footer{
	position: relative;
	overflow-x: hidden;

	a {
		text-decoration: none;
	}

	.image {
		height: 245px;
		background: url('../assets/images/clouds.svg');
		background-repeat: repeat-x;
		background-position: center;
	}

	.content {
		background: $dark-green;
		display: grid;
		grid-template-areas:
		'fb   email'
		'desc desc'
		'logo logo'
		'copy copy';

		@media (max-width: $smartphones) {
			grid-template-areas:
			'fb'
			'email'
			'desc'
			'logo'
			'copy';
		}

		.link {
			justify-self: center;

			@media (max-width: $smartphones) {
				justify-self: left;
				margin-bottom: 2em;
				position: relative;
				left: 7%;
			}

			&:nth-child(1) {
				grid-area: fb;
			}

			&:nth-child(2) {
				grid-area: email;
			}

			.container {
				display: flex;

				.text {
					padding-left: 1.5em;
					display: flex;
					flex-direction: column;
					justify-content: center;

					p {
						color: #8BBE47;
						font-size: 1.75vw;
						font-weight: 500;
						letter-spacing: .5px;

						@media (max-width: $tablets) {
							font-size: 2.5vw;
						}

						@media (max-width: $smartphones) {
							font-size: 4vw;
						}
					}

					span {
						color: $green;
						font-size: 1.25em;
						font-weight: 300;

						@media (max-width: $tablets) {
							font-size: 1.7vw;
						}

						@media (max-width: $smartphones) {
							font-size: 3.25vw;
						}
					}
				}
			}

			img {
				width: 9vw;
				height: 9vw;

				@media (max-width: $tablets) {
					width: 80px;
					height: 80px;
				}

				@media (max-width: $smartphones) {
					width: 60px;
					height: 60px;
				}
			}
		}

		.description {
			grid-area: desc;
			padding: 1em 0;
			color: $green;
			text-align: center;
			font-size: 1.5vw;
			font-weight: 300;
			letter-spacing: 1px;

			@media (max-width: $tablets) {
				font-size: 3vw;
			}

			@media (max-width: $smartphones) {
				font-size: 5vw;
			}
		}

		.zwolnieni-logo {
			grid-area: logo;
			text-align: center;

			img {
				width: 400px;
				height: 150px;
				opacity: .8;

				@media (max-width: $smartphones) {
					width: 200px;
					height: 75px;
				}
			}
		}

		.copyright {
			grid-area: copy;
			color: $green;
			font-size: 1.25vw;
			font-weight: 300;
			display: flex;
			justify-content: flex-end;
			position: relative;
			bottom: 100%;

			@media (max-width: $tablets) {
				position: static;
				margin-top: 2em;
				justify-content: center;
				font-size: 3vw;
			}

			@media (max-width: $smartphones) {
				justify-content: center;
				font-size: 4vw;
			}
		}
	}
}

section {
	padding: ($padding-main / 4) $padding-main;

	@media (max-width: $tablets) {
		padding: ($padding-main / 3) ($padding-main / 2);
	}

	@media (max-width: $smartphones) {
		padding: ($padding-main / 4);
	}
}

</style>