<template>
	<div class="star" :class="starType">
		<span v-for="itemClass in itemClasses" :class="itemClass" class="star-item"></span>
	</div>
</template>

<script type="text/script">
	const LENGTH = 5
	const CLS_HALF = 'half'
	const CLS_OFF = 'off'
	const CLS_ON = 'on'
	export default {
  props: {
    size: {
      type: Number
    },
    score: {
      type: Number
    }
  },
  computed: {
    starType () {
      return 'star-' + this.size
    },
    itemClasses () {
      let result = []
      let score = Math.floor(this.score * 2) / 2
      let hasDecimal = score % 1 !== 0
      let integer = Math.floor(score)
      for (let i = 0; i < integer; i++) {
        result.push(CLS_ON)
      }
      if (hasDecimal) {
        result.push(CLS_HALF)
      }
      while (result.length < LENGTH) {
        result.push(CLS_OFF)
      }
      return result
    }
  }
	}
</script>

<style lang="scss">
	@import '../../common/sass/mixin.scss';
	.star{
		font-size: 0;
		.star-item{
			display: inline-block;
			background-repeat: no-repeat;
		}
		&.star-48{
			.star-item{
				width: 20px;
				height: 20px;
				margin-right: 22px;
				background-size: 20px 20px;
				&:last-child{
					margin-right: 0;
				}
				&.on{
					@include bg-media('star48_on')
				}
				&.off{
					@include bg-media('star48_off')
				}
				&.half{
					@include bg-media('star48_half')
				}
			}
		}
		&.star-36{
			.star-item{
				width: 15px;
				height: 15px;
				margin-right: 6px;
				background-size: 15px 15px;
				&:last-child{
					margin-right: 0;
				}
				&.on{
					@include bg-media('star36_on')
				}
				&.off{
					@include bg-media('star36_off')
				}
				&.half{
					@include bg-media('star36_half')
				}
			}
		}
		&.star-24{
			.star-item{
				width: 10px;
				height: 10px;
				margin-right: 3px;
				background-size: 10px 10px;
				&:last-child{
					margin-right: 0;
				}
				&.on{
					@include bg-media('star24_on')
				}
				&.off{
					@include bg-media('star24_off')
				}
				&.half{
					@include bg-media('star24_half')
				}
			}
		}
	}
</style>