<template>
	<nav id="navbar">
		<div class="navElements">
      <div class="navElementsContainer">
        <a v-on:click="navAnimation()" class="navElement">Home</a>
        <a v-on:click="navAnimation()" class="navElement">Lorem ipsum</a>
        <a v-on:click="navAnimation()" class="navElement">Lorem ipsum</a>
        <a v-on:click="navAnimation()" class="navElement">Lorem ipsum</a>
      </div>
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
		this.navTimeline.to('.navElements',0.5,{
			x: '-100%',
		})
				.to('.topMenuBtn',{
					top: '50%',
					rotate: '45deg'
				},'-=0.25')
				.to('.bottomMenuBtn',{
					bottom: '50%',
					rotate: '-45deg'
				}, '-=0.5')
				.to('.navElement',{
					opacity: 1,
					stagger: 0.05,
				}, '-=0.5').reverse()
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
		right: 0;
		width: 100%;
		height: 100vh;
		transition: .3s ease;
		z-index: 10000;

		.navElements{
			position: absolute;
			width: 100%;
			height: 100%;
			top: 0;
			right: -100%;
			background: #000;
			opacity: 1;
			background: $light-green;
			padding-right: 40px;
			padding-left: 40px;
			padding-top: 50px;
			display: block;
			justify-content: space-around;

      .navElementsContainer{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        
		.navElement{
          display: block;
          margin: 10px;
          text-align: center;
          line-height: 100px;
          font-size: 20px;
		  background-color: darken($light-green, 20);
		  border-radius: 50px;
          height: 100px;
          width: 280px;
          color: lighten($yellow , 5);
          cursor: pointer;
          opacity: 0;

          &:hover{
            color: $green;
          }
        }
      }
		}


		.menuBtn{
			position: absolute;
			height: 50px;
			width: 50px;
			border-top-left-radius: 50px;
			border-bottom-left-radius: 50px;
			right: 0px;
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

  @media(min-width: 768px){
    #navbar{
      width: 350px;
    }
  }

  @media(min-width: 1025px){
    #navbar{
      width: 700px;
	  height: auto;
      
	  .navElements{
        height: 50px;
        border-radius: 200px;
        width: 700px;

        .navElementsContainer{
          display: flex;
          justify-content: space-around;
          width: 100%;
          padding-left: 40px;
          padding-right: 40px;

          .navElement{
            border: none;
            margin: 0;
            display: initial;
            font-size: 15px;
            height: 20px;
            line-height: 20px;
            width: auto;
			background-color: transparent;
          }
        }
      }
    }
  }

	:focus{
		outline: none;
	}
}

</style>