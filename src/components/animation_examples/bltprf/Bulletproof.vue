<template>
  <div>
    <section class="kinetic" :class="{'mobile--height': mobile}" v-if="kinetic">
      <div class="hero_bg" :class="{'mobile--height': mobile}">
        <div class="characters"></div>
        <div class="copy_mates"></div>
        <div class="copy_mission"></div>
        <div class="sky-one"></div>
        <div class="flares"></div>
        <div class="copy_starts-tonight"></div>
        <div class="copy_bullet"></div>
        <div class="copy_proof"></div>
        <div class="copy_names"></div>
        <div class="top-bar"></div>
        <div class="bottom-bar"></div>
      </div>
    </section>
    <section class="fallback" v-else>
      <img src="./images/fallback.gif" alt="Bulletproof">
    </section>
  </div>
</template>
<script>
export default {
  name: "BulletproofAnimation",
  props: {
    isKineticView: Boolean,
    isMobile: Boolean
  },
  mounted() {
    this.kinetic = this.isKineticView;
    this.mobile = this.isMobile;
  },
  data() {
    return {
      kinetic: null,
      mobile: null
    }
  },
  watch: {
    isKineticView() {
      this.kinetic = this.isKineticView;
    },
    isMobile() {
      this.mobile = this.isMobile;
    }
  }
}
</script>
<style scoped>

  .fallback img {
    max-width: 100%;
    height: auto;
  }

		.hero_wrapper {
			display: block;
			overflow: hidden ;
			visibility: visible ;
		}
		.hide {
			display: none ; 
			visibility: hidden ; 
		}

		.hero_bg {
			background-color: #ffffff;
			background-size: 100%;
			z-index: 1;
			position: relative;

      height: 830px;
      overflow: hidden;
		}

		.mobile--height {
			height: 550px;
		}

		.characters {
			background: url('images/characters.png');
			background-position: center bottom;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 2;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: characters 10s infinite linear;
			-webkit-animation: characters 10s infinite linear;
		}
		.copy_mates {
			background: url('images/copy_mates.png');
			background-position: center bottom;
			background-repeat: no-repeat ;
			background-size: 66%;
			z-index: 3;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: copy_mates 10s infinite linear;
			-webkit-animation: copy_mates 10s infinite linear;
		}

		.copy_mission {
			background: url('images/copy_mission.png');
			background-position: center bottom;
			background-repeat: no-repeat ;
			background-size: 66%;
			z-index: 3;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: copy_mission 10s infinite linear;
			-webkit-animation: copy_mission 10s infinite linear;
		}

		.sky-one {
			background: url('images/sky-one.png');
			background-position: center bottom;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 4;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: sky-one 10s infinite linear;
			-webkit-animation: sky-one 10s infinite linear;
		}

		.flares {
			background: url('images/flares.png');
			background-position: center bottom;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 4;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: flares 10s infinite linear;
			-webkit-animation: flares 10s infinite linear;
		}

		.copy_starts-tonight {
			background: url('images/copy_starts-tonight.png');
			background-position: center bottom;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 3;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: copy_starts-tonight 10s infinite linear;
			-webkit-animation: copy_starts-tonight 10s infinite linear;
		}

		.copy_bullet {
			background: url('images/copy_bullet.png');
			background-position: center top;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 2;
			overflow: hidden;
			opacity: 0;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: copy_bullet 10s infinite linear;
			-webkit-animation: copy_bullet 10s infinite linear;
		}

		.copy_proof {
			background: url('images/copy_proof.png');
			background-position: center top;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 1;
			overflow: hidden;
			position: absolute;
			height: 100%;
			width: 100%;
			animation: copy_proof 10s infinite linear;
			-webkit-animation: copy_proof 10s infinite linear;
		}

		.copy_names {
			background: url('images/copy_names.png');
			background-position: left top;
			background-repeat: no-repeat ;
			background-size: 100%;
			z-index: 1;
			overflow: hidden;
			position: absolute;
			left: 0;
			height: 100%;
			width: 100%;
			animation: copy_names 10s infinite linear;
			-webkit-animation: copy_names 10s infinite linear;
		}

		.top-bar {
			background-color: #000000;
			z-index: 10;
			position: absolute;
			height: 15px;
			animation: top-bar 10s infinite ease-out;
			-webkit-animation: top-bar 10s infinite ease-out;
		}

		.bottom-bar {
			background-color: #000000;
			z-index: 1;
			position: absolute;
			height: 15px;
			animation: bottom-bar 10s infinite ease-out;
			-webkit-animation: bottom-bar 10s infinite ease-out;
		}
	
	@keyframes characters {
		0% {bottom: -7%; left: 1%; transform: scale(1.54); }
		3% {bottom: -7%; left: 1%; transform: scale(1.54); }
		6% {bottom: -6%; left: 1%; transform: scale(1.45); }
		24% {bottom: -6%; left: 1%; transform: scale(1.39); }
		27% {bottom: -1%; left: 0%; transform: scale(1.23); }
		51% {bottom: -1%; left: 0%; transform: scale(1.18); }
		54% {bottom: -7%; left: 1%; transform: scale(1.00); }
		100% {bottom: -7%; left: 1%; transform: scale(1.02); }
	}

	@-webkit-keyframes characters {
		0% {bottom: -7%; left: 1%; transform: scale(1.54); }
		3% {bottom: -7%; left: 1%; transform: scale(1.54); }
		6% {bottom: -6%; left: 1%; transform: scale(1.45); }
		24% {bottom: -6%; left: 1%; transform: scale(1.39); }
		27% {bottom: -1%; left: 0%; transform: scale(1.23); }
		51% {bottom: -1%; left: 0%; transform: scale(1.18); }
		54% {bottom: -7%; left: 1%; transform: scale(1.00); }
		100% {bottom: -7%; left: 1%; transform: scale(1.02); }
	}

	@keyframes copy_mates {
		0% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		3% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		6% {bottom: -5%; opacity: 1; transform: scale(0.70); }
		25% {bottom: -5%; opacity: 1; transform: scale(0.69); }
		28% {bottom: -5%; opacity: 0; transform: scale(0.3); }
		100% {bottom: -5%; opacity: 0; transform: scale(0.3); }
	}

	@-webkit-keyframes copy_mates {
		0% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		3% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		6% {bottom: -5%; opacity: 1; transform: scale(0.70); }
		25% {bottom: -5%; opacity: 1; transform: scale(0.69); }
		28% {bottom: -5%; opacity: 0; transform: scale(0.3); }
		100% {bottom: -5%; opacity: 0; transform: scale(0.3); }
	}

	@keyframes copy_mission {
		0% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		24% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		27% {bottom: -5%; opacity: 1; transform: scale(0.70); }
		51% {bottom: -5%; opacity: 1; transform: scale(0.69); }
		54% {bottom: -5%; opacity: 0; transform: scale(0.3); }
		100% {bottom: -5%; opacity: 0; transform: scale(0.3); }
	}

	@-webkit-keyframes copy_mission {
		0% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		24% {bottom: -5%; opacity: 0; transform: scale(2.0); }
		27% {bottom: -5%; opacity: 1; transform: scale(0.70); }
		51% {bottom: -5%; opacity: 1; transform: scale(0.69); }
		54% {bottom: -5%; opacity: 0; transform: scale(0.3); }
		100% {bottom: -5%; opacity: 0; transform: scale(0.3); }
	}

	@keyframes sky-one {
		0% {bottom: -25%; opacity: 0; transform: scale(2.0); }
		51% {bottom: -25%; opacity: 0; transform: scale(2.0); }
		54% {bottom: -27%; opacity: 1; transform: scale(0.33); }
		100% {bottom: -27%; opacity: 1; transform: scale(0.34); }
	}

	@-webkit-keyframes sky-one {
		0% {bottom: -25%; opacity: 0; transform: scale(2.0); }
		51% {bottom: -25%; opacity: 0; transform: scale(2.0); }
		54% {bottom: -27%; opacity: 1; transform: scale(0.33); }
		100% {bottom: -27%; opacity: 1; transform: scale(0.34); }
	}

	@keyframes flares {
		0% {bottom: 0%; opacity: 0; transform: scale(2.0); }
		51% {bottom: 0%; opacity: 0; transform: scale(2.0); }
		54% {bottom: 0%; opacity: 1; transform: scale(1.0); }
		100% {bottom: 0%; opacity: 1; transform: scale(1.01); }
	}

	@-webkit-keyframes flares {
		0% {bottom: 0%; opacity: 0; transform: scale(2.0); }
		51% {bottom: 0%; opacity: 0; transform: scale(2.0); }
		54% {bottom: 0%; opacity: 1; transform: scale(1.0); }
		100% {bottom: 0%; opacity: 1; transform: scale(1.01); }
	}

	@keyframes copy_starts-tonight {
		0% {bottom: -25%; opacity: 0; transform: scale(0.31); }
		53% {bottom: -25%; opacity: 0; transform: scale(0.31); }
		55% {bottom: -25%; opacity: 1; transform: scale(0.31); }
		65% {bottom: -20%; opacity: 1; transform: scale(0.31); }
		100% {bottom: -20%; opacity: 1; transform: scale(0.32); }
	}

	@-webkit-keyframes copy_starts-tonight {
		0% {bottom: -25%; opacity: 0; transform: scale(0.31); }
		53% {bottom: -25%; opacity: 0; transform: scale(0.31); }
		55% {bottom: -25%; opacity: 1; transform: scale(0.31); }
		65% {bottom: -20%; opacity: 1; transform: scale(0.31); }
		100% {bottom: -20%; opacity: 1; transform: scale(0.32); }
	}

	@keyframes copy_bullet {
		0% {top: 0%; opacity: 0; transform: scale(0.85); }
		52% {top: 0%; opacity: 0; transform: scale(0.85); }
		53% {top: -2%; opacity: 1; transform: scale(0.85); }
		54% {top: -5%; opacity: 1; transform: scale(0.89); }
		55% {top: -3%; opacity: 1; transform: scale(0.87); }
		100% {top: -3%; opacity: 1; transform: scale(0.89); }
	}

	@-webkit-keyframes copy_bullet {
		0% {top: 0%; opacity: 0; transform: scale(0.85); }
		52% {top: 0%; opacity: 0; transform: scale(0.85); }
		53% {top: -2%; opacity: 1; transform: scale(0.85); }
		54% {top: -5%; opacity: 1; transform: scale(0.89); }
		55% {top: -3%; opacity: 1; transform: scale(0.87); }
		100% {top: -3%; opacity: 1; transform: scale(0.89); }
	}

	@keyframes copy_proof {
		0% {top: 13%; opacity: 0; transform: scale(0.85); }
		53% {top: 13%; opacity: 0; transform: scale(0.82); }
		54% {top: 13%; opacity: 1; transform: scale(0.82); }
		56% {top: 13%; opacity: 1; transform: scale(0.87); }
		100% {top: 13%; opacity: 1; transform: scale(0.89); }
	}

	@-webkit-keyframes copy_proof {
		0% {top: 13%; opacity: 0; transform: scale(0.85); }
		53% {top: 13%; opacity: 0; transform: scale(0.82); }
		54% {top: 13%; opacity: 1; transform: scale(0.82); }
		56% {top: 13%; opacity: 1; transform: scale(0.87); }
		100% {top: 13%; opacity: 1; transform: scale(0.89); }
	}

	@keyframes copy_names {
		0% {top: -23%; left: -21% ; opacity: 0; transform: scale(0.45); }
		54% {top: -23%; left: -21% ; opacity: 0; transform: scale(0.45); }
		55% {top: -23%; left: -21% ; opacity: 1; transform: scale(0.45); }
		59% {top: -26.8%; left: -21% ; opacity: 1; z-index: 1; transform: scale(0.45); }
		65% {top: -26.8%; left: -21% ; opacity: 1; z-index: 3; transform: scale(0.45); }
		100% {top: -26.8%; left: -21% ; opacity: 1; z-index: 3; transform: scale(0.46); }
	}

	@-webkit-keyframes copy_names {
		0% {top: -23%; left: -21% ; opacity: 0; transform: scale(0.45); }
		54% {top: -23%; left: -21% ; opacity: 0; transform: scale(0.45); }
		55% {top: -23%; left: -21% ; opacity: 1; transform: scale(0.45); }
		59% {top: -26.8%; left: -21% ; opacity: 1; z-index: 1; transform: scale(0.45); }
		65% {top: -26.8%; left: -21% ; opacity: 1; z-index: 3; transform: scale(0.45); }
		100% {top: -26.8%; left: -21% ; opacity: 1; z-index: 3; transform: scale(0.46); }
	}

	@keyframes top-bar {
		0% {left: 54%; opacity: 0; top: 1.3%; width: 7%; transform: scale(1); }
		54% {left: 54%; opacity: 0; top: 1.3%; width: 7%; transform: scale(1); }
		55% {left: 54%; opacity: 1; top: 1.3%; width: 7%; transform: scale(1); }
		67% {left: 54%; opacity: 1; top: 1.3%; }
		90% {opacity: 1; width: 40%; }
		100% {left: 54%; opacity: 1; top: 1.3%; width: 40.5%; transform: scale(1); }
	}

	@-webkit-keyframes top-bar {
		0% {left: 54%; opacity: 0; top: 1.3%; width: 7%; transform: scale(1); }
		54% {left: 54%; opacity: 0; top: 1.3%; width: 7%; transform: scale(1); }
		55% {left: 54%; opacity: 1; top: 1.3%; width: 7%; transform: scale(1); }
		67% {left: 54%; opacity: 1; top: 1.3%; }
		90% {opacity: 1; width: 40%; }
		100% {left: 54%; opacity: 1; top: 1.3%; width: 40.5%; transform: scale(1); }
	}

	@keyframes top-bar-mob {
		0% {left: 54%; opacity: 0; top: 0.8%; width: 7%; transform: scale(1); }
		54% {left: 54%; opacity: 0; top: 0.8%; width: 7%; transform: scale(1); }
		55% {left: 54%; opacity: 1; top: 0.8%; width: 7%; transform: scale(1); }
		67% {left: 54%; opacity: 1; top: 0.8%; }
		90% {opacity: 1; width: 40%; }
		100% {left: 54%; opacity: 1; top: 0.8%; width: 40.5%; transform: scale(1); }
	}

	@-webkit-keyframes top-bar-mob {
		0% {left: 54%; opacity: 0; top: 0.8%; width: 7%; transform: scale(1); }
		54% {left: 54%; opacity: 0; top: 0.8%; width: 7%; transform: scale(1); }
		55% {left: 54%; opacity: 1; top: 0.8%; width: 7%; transform: scale(1); }
		67% {left: 54%; opacity: 1; top: 0.8%; }
		90% {opacity: 1; width: 40%; }
		100% {left: 54%; opacity: 1; top: 0.8%; width: 40.5%; transform: scale(1); }
	}

	@keyframes top-bar-mob-alt {
		0% {left: 54%; opacity: 0; top: 1%; width: 7%; transform: scale(1); }
		54% {left: 54%; opacity: 0; top: 1%; width: 7%; transform: scale(1); }
		55% {left: 54%; opacity: 1; top: 1%; width: 7%; transform: scale(1); }
		67% {left: 54%; opacity: 1; top: 1%; }
		90% {opacity: 1; width: 40%; }
		100% {left: 54%; opacity: 1; top: 1%; width: 40.5%; transform: scale(1); }
	}

	@-webkit-keyframes top-bar-mob-alt {
		0% {left: 54%; opacity: 0; top: 1%; width: 7%; transform: scale(1); }
		54% {left: 54%; opacity: 0; top: 1%; width: 7%; transform: scale(1); }
		55% {left: 54%; opacity: 1; top: 1%; width: 7%; transform: scale(1); }
		67% {left: 54%; opacity: 1; top: 1%; }
		90% {opacity: 1; width: 40%; }
		100% {left: 54%; opacity: 1; top: 1%; width: 40.5%; transform: scale(1); }
	}

	@keyframes bottom-bar {
		0% {right: 7%; opacity: 0; top: 35.5%; width: 2%; transform: scale(1); }
		53% {right: 7%; opacity: 0; top: 35.5%; width: 2%; transform: scale(1); }
		54% {right: 7%; opacity: 1; top: 35.5%; width: 2%; transform: scale(1); }
		59% {right: 7%; opacity: 1; top: 35.5%; width: 83%; transform: scale(1); }
		67% {right: 7%; opacity: 1; }
		90% {opacity: 1; width: 86.9%; }
		100% {right: 7%; opacity: 1; top: 35.5%; width: 87.3%; transform: scale(1); }
	}

	@-webkit-keyframes bottom-bar {
		0% {right: 7%; opacity: 0; top: 35.5%; width: 2%; transform: scale(1); }
		53% {right: 7%; opacity: 0; top: 35.5%; width: 2%; transform: scale(1); }
		54% {right: 7%; opacity: 1; top: 35.5%; width: 2%; transform: scale(1); }
		59% {right: 7%; opacity: 1; top: 35.5%; width: 83%; transform: scale(1); }
		67% {right: 7%; opacity: 1; }
		90% {opacity: 1; width: 86.9%; }
		100% {right: 7%; opacity: 1; top: 35.5%; width: 87.3%; transform: scale(1); }
	}
</style>
