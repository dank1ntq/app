<template>
  <header>
    <div class="header">
      <h1>{{ title }}</h1>
      <div class="header__icon">
        <span class="header__icon-back" @click="onGoScreen"></span>
      </div>
    </div>
  </header>
</template>

<script>
  import animation from '../animation'

  export default {
    name: 'header',
    props: {
      title: {
        type: String,
        required: true
      }
    },
    methods: {
      onGoScreen: function () {
        if (this.$store.state.currentFloatScreen) {
          this.$store.commit ( 'updateFloatScreen', '' )
        } else {
          this.$store.dispatch ( 'goScreen', animation.mainScreen )
        }
      }
    }
  }
</script>

<style>
  .header {
    background: #fff;
    position: relative;
    box-shadow: 0 2px 16px 0px rgba(0,0,0,0.1);
    -webkit-box-shadow: 0 2px 16px 0px rgba(0,0,0,0.1);
    -moz-box-shadow: 0 2px 16px 0px rgba(0,0,0,0.1);
  }

  .header h1 {
    font-size: 16px;
    font-weight: 600;
    line-height: 56px;
    text-align: center;
  }

  .header__icon {
    position: absolute;
    left: 16px;
    top: 12px;
  }

  .header__icon-back {
    display: block;
    width: 32px;
    height: 32px;
    background: url("/static/img/icons/icon_back.png") no-repeat;
    cursor: pointer;
  }

</style>
