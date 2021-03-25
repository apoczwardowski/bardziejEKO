<template>
	<nav id="navbar">
		<div class="navElementsContainer">
			<a v-on:click="navAnimation()" class="navElement">Home</a>
			<a v-on:click="navAnimation()" class="navElement">Lorem ipsum</a>
			<a v-on:click="navAnimation()" class="navElement">Lorem ipsum</a>
			<a v-on:click="navAnimation()" class="navElement">Lorem ipsum</a>
		</div>
    <button v-on:click="navAnimation()" class="menuBtn">
      <div class="lineMenuBtn topMenuBtn"></div>
      <div class="lineMenuBtn bottomMenuBtn"></div>
    </button>
  </nav>
</template>

<script>
/* eslint-disable */
import gsap from "gsap"

export default {
	name: 'Navbar',
	data(){
		return {
			navTimeline: new gsap.timeline({
				defaults:{
					duration: 0.5,
					ease: "power4.inOut",
				}
			})
		}

	},
	methods: {
		navAnimation: function (){
			this.navTimeline.reversed(!this.navTimeline.reversed())
		}
	},

	mounted(){
		this.navTimeline.to('.navElementsContainer',{
			height: '50px',
			right: 0
		})
				.to('.topMenuBtn',{
					top: '50%',
					rotate: '45deg'
				}, '-=0.5')
				.to('.bottomMenuBtn',{
					bottom: '50%',
					rotate: '-45deg'
				}, '-=0.5')
				.to('.navElement',{
					opacity: 1,
					stagger: 0.05,
				},'-=0.25')
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
@media(min-width: 280px){
	#navbar {
		position: fixed;
		right: 25px;
		width: 50vw;
		min-width: 500px;

		.navElementsContainer{
			position: absolute;
			top: 0;
			right: -150%;
			background: #000;
			width: 100%;
			height: 50px;
			opacity: 1;
			background: $light-green;
			padding-right: 40px;
			padding-left: 40px;
			border-radius: 0px 0px 0px 200px;
			display:  flex;
			justify-content: space-around;


			.navElement{
				line-height: 50px;
				height: 100%;
				color: $dark-green;
				cursor: pointer;
				font-size: 15px;
				opacity: 0;

				&:hover{
					color: $green;
				}
			}
		}


		.menuBtn{
			position: absolute;
			height: 50px;
			width: 50px;
			border-top-left-radius: 50px;
			border-bottom-left-radius: 50px;
			right: -25px;
			top: 0;
			border: none;
			background: $light-green;
			cursor: pointer;
			transition: .3s ease;

			&:hover{
				transform: scale(1.05);
			}

			.lineMenuBtn {
				position: absolute;
				height: 3px;
				width: 30px;
				background-color: $yellow;
				border-radius: 50px;
				left: 50%;
			}

			.topMenuBtn{
				top: 40%;
				transform: translate(-50%,-50%);
			}

			.bottomMenuBtn{
				bottom: 40%;
				transform: translate(-50%,50%);
			}
		}
	}

	:focus{
		outline: none;
	}
}

</style>