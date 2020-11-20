<template>
  <div class="main">
    <div class="config">

      <div class="pallet">
        <div
          v-for="item in colors"
          class="color"
          :class="{'active' : color == item.color}"
          :key="item.name"
          :style="`background-color: ${item.color}`"
          @click="change(item)"
        >
        </div>
      </div>
    </div>
    <div class="view">
      <div class="draw">
        <div class="crew-shadow" :style="`background-color: ${getColor}`"></div>
        <div class="crew">
          <div class="legs-shadow"></div>
          <div class="legs"></div>
          <div class="back"></div>
          <div class="glass"></div>
          <!-- <div class="shadow"></div> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AmongUs',
  data() {
    return {
      color: '#c51111',
      colors: [
              {name: 'Red', color:'#c51111'},
              {name: 'Blue', color: '#132ed1'},
              {name: 'DarkGreen', color:'#117f2d'},
              {name: 'Pink', color: '#fb69be'},
              {name: 'Orange', color: '#e8790e'},
              {name: 'Yellow', color: '#f5f557'},
              {name: 'black', color: '#3e474e'},
              {name: 'White', color: '#d6e1f3'},
              {name: 'Purple', color: '#6d3ec0'},
              {name: 'Brown', color: '#764a1d'},
              {name: 'Cyan', color: '#28eae1'},
              {name: 'LightGreen', color: '#45d633'},
            ]
    }
  },
  methods:{
    change(opt){
      this.color = opt.color;
      let root = document.documentElement;
      root.style.setProperty('--color',this.color)
    }
  },
  computed: {
    getColor(){
      return this.color;
    }
  },
  mounted(){
    let root = document.documentElement;
    root.style.setProperty('--color',this.color)
  }
}
</script>

<style scoped>
:root{
  --color: '#c51111'
}
@media (max-device-width: 520px ){
  .main{
    flex-direction: column-reverse;
  }
  .config{
    width: 100%;
    height: 50vh;
    display: flex;
  }
  .view{
    /* min-width: 50vw; */
    width: 100%;
    height: 50vh;
    display: flex;
  }
  .active{
    transform: scale(1.1);
  }
  .draw{
    margin: 0 auto;
    position: relative;
    left: -54px !important;
    top: -16px;
    filter: drop-shadow(2px 1px 3px rgba(255,255,255, 0.4)) drop-shadow(-2px -1px 3px rgba(255,255,255, 0.4));
  }
}
  .main{
    height: 100vh;
    background-color: #FFDE2A;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .config{
    background-color: #778c79;
    padding: 1rem;
    display: flex;
  }
  .view{
    background-image: url("../assets/background.jpg");
    background-size: contain;
  }
  .pallet{
    background-color: #9fbba2;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: .6rem;
    width: 100%;
    place-items: center;
    padding: .3rem .5rem;
    border-radius: 4px;
  }
  .color{
    cursor: pointer;
    border-radius: 12px;
    /* border: 5px solid black; */
    filter:
      drop-shadow(0px 4px 0px black)
      drop-shadow(-4px 0px 0px black)
      drop-shadow(0 -4px 0px black)
      drop-shadow(4px 0px 0px black);

    position: relative;
    width: 50%;
    height: 0;
    padding-bottom: 50%;
    max-height: 150px;
  }
  .active{
    transition: .2s;
    transform: scale(1.2);
  }

@media (min-width: 521px ){
  .config{
    background-color: #778c79;
    min-width: 50vw;
    min-height: 100vh;
    padding: 1rem;
    display: flex;
  }
  .pallet{
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: .6rem;
    width: 100%;
    place-items: center;
    padding: .3rem .5rem;
    border-radius: 4px;
  }
  .color{
    cursor: pointer;
    border-radius: 12px;
    /* border: 5px solid black; */
    filter:
      drop-shadow(0px 4px 0px black)
      drop-shadow(-4px 0px 0px black)
      drop-shadow(0 -4px 0px black)
      drop-shadow(4px 0px 0px black);

    position: relative;
    width: 50%;
    height: 0;
    padding-bottom: 50%;
    max-height: 150px;
  }

  .active{
    transition: .2s;
    transform: scale(1.3);
  }

  .view{
    min-width: 50vw;
    min-height: 100vh;
    display: flex;
  }

}
  .draw{
    margin: 0 auto;
    position: relative;
    left: -6vw;
    filter: drop-shadow(2px 1px 3px rgba(255,255,255, 0.4)) drop-shadow(-2px -1px 3px rgba(255,255,255, 0.4));
  }
  .crew{
      /* background-color: #840931; */
      height: 200px;
      width: 140px;
      position: absolute;
      margin: auto;
      left: 0;
      right: 0;
      bottom: 0;
      top: 0;
      border: 10px solid black;
      border-bottom: none;
      border-radius: 60px 80px 0 0;
      z-index: 1;
  }
  .crew:after{
      content: "";
      position: absolute;
      width: 92%;
      height: 85%;
      background-color: var(--color);
      /* background-color: #EA1616; */
      top: 2.5px;
      left: 6px;
      border-radius: 58% 70% 28% 42% / 28% 56% 88% 89%;
  }
  .crew-shadow{
    filter: hue-rotate(-19deg) brightness(0.75) grayscale(0.38);
    height: 200px;
    width: 140px;
    position: absolute;
    margin: auto;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    border: 10px solid black;
    border-bottom: none;
    border-radius: 60px 80px 0 0;
    z-index: 1;
  }

  .legs{
      height: 50px;
      width: 60px;
      /* background-color: #840931; */
      background-color: var(--color);
      filter: hue-rotate(-19deg) brightness(0.75) grayscale(0.38);
      position: absolute;
      bottom: -50px;
      left: -10px;
      border: 10px solid black;
      border-top: none;
      border-radius: 0 0 22px 22px;
      z-index: 1;
  }
  .legs:before{
      content: "";
      height: 45px;
      width: 60px;
      /* background-color: #840931; */
      background-color: var(--color);
      position: absolute;
      right: -90px;
      border: 10px solid black;
      border-top: none;
      border-radius: 0 0 22px 22px;
  }
  .legs:after{
      content: "";
      height: 10px;
      width: 55px;
      background-color: black;
      position: absolute;
      top: -10px;
      left: 40px;
      border-radius: 0 0 10px 0;
  }

  .back{
    height: 120px;
    width: 35px;
    /* background-color: #EA1616; */
    background-color: var(--color);
    border: 10px solid black;
    position: absolute;
    left: -45px;
    top: 65px;
    border-right: none;
    border-radius: 20px 0 0 20px;
  }
  .back:before{
      content: "";
      height: 78px;
      width: 26px;
      /* background-color: #840931; */
      background-color: var(--color);
      filter: hue-rotate(-19deg) brightness(0.75) grayscale(0.38);
      position: absolute;
      bottom: -1px;
      left: -1px;
      border-radius: 12px 0 0 8px;
  }

  .glass{
      height: 75px;
      width: 110px;
      background-color: #225381;
      z-index: 2;
      position: absolute;
      top: 30px;
      left: 40px;
      border: 10px solid black;
      border-radius: 25px 50px 30px 30px;
  }
  .glass:before{
      content: "";
      position: absolute;
      height: 65%;
      width: 85%;
      background-color: #71D4EC;
      border-radius: 0 28px 3px 30px;
      right: 0;
      top: 0;
  }
  .glass:after{
      content: "";
      position: absolute;
      width: 45%;
      height: 22%;
      background-color: #F7F7F7;
      left: 39px;
      top: 5px;
      border-radius: 10px;
      transform: rotate(6deg);
  }

  .shadow{
      height: 40px;
      width: 210px;
      background-color: rgba(153, 130, 0, .2);
      position: absolute;
      bottom: -60px;
      right: -40px;
      border-radius: 50%;
      z-index: 0;
  }

</style>
