<template>
  <div class="whole">
    <div class="top">
      <div class="topic">
        <h1>TODO</h1>
        <img src="@/assets/icon-sun.svg" alt="">
      </div>
    </div>
    <div class="input">
      <form action="" @submit.prevent="pusher">
        <input type="text" id="list_input" placeholder="Create a new todo..." v-model="text">
      </form>


      <!-- <button v-on:click="appear" class="butt"> -->
      <img src="@/assets/Ovalcard.svg" alt="" class="butt">
      <!-- <img src="@/assets/Group4.svg" alt="" class="unshow" :class="[toggle ? unshow2 : '']"> -->
      <!-- </button> -->

    </div>
    <div class="bottom"></div>
    <div class="fun">
      <div class="wrapper">

        <div v-for="(words, index) in filterList" :key="words.index" class="pop">
          <div class="list">

            <h2 class="textList" :style="[words.completed ? {
              'text-decoration': 'line-through', 'height': '18px',
              'font-style': 'normal',
              'font-weight': '400',
              'font-size': '18px',
              'line-height': '18px',
              'letter-spacing': '-0.25px',
              'text-decoration-line': 'line-through',
            
              'color': '#4D5067',
            
            } : { 'text-decoration': 'none' }]">{{ words.value }}</h2>
            <button v-on:click="appear1(words)" class="butto">
              <img :src="words.image" alt="">
            </button>
          </div>
          <hr id="hr">
        </div>
        <div class="lister">
          <h4>{{ this.activeList.length }} items left</h4>
          <div id="comm">
            <h6 @click="All" :style="[state === 'all' ? { color: '#3A7CFD' } : { color: '#5b5e7e' }]">All</h6>
            <h6 @click="Active" :style="[state === 'active' ? { color: '#3A7CFD' } : { color: '#5b5e7e' }]">Active
            </h6>
            <h6 @click="Complete" :style="[state === 'completed' ? { color: '#3A7CFD' } : { color: '#5b5e7e' }]">
              Completed</h6>
          </div>
          <h5 @click="clearCompleted">Clear completed</h5>
        </div>
        <div id="coma">
          <h6 @click="All" :style="[state === 'all' ? { color: '#3A7CFD' } : { color: '#5b5e7e' }]">All</h6>
          <h6 @click="Active" :style="[state === 'active' ? { color: '#3A7CFD' } : { color: '#5b5e7e' }]">Active
          </h6>
          <h6 @click="Complete" :style="[state === 'completed' ? { color: '#3A7CFD' } : { color: '#5b5e7e' }]">
            Completed</h6>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
// import { url } from 'inspector'

export default {
  name: 'HomeView',
  data() {
    return {
      // toggle: false,
      toggle1: false,
      show2: 'show2',
      show1: 'show1',
      unshow2: 'unshow2',
      unshow1: 'unshow1',
      blue: 'blue',
      text: "",
      List: [],
      state: 'all'
    }
  },

  methods: {
    // appear() {
    //   this.toggle = !this.toggle
    // },
    appear1(obj) {
      this.toggle1 = !this.toggle1
      if (this.toggle1) {
        obj.image = require("@/assets/Group4.svg")
        obj.completed = true

      } else {
        obj.image = require("@/assets/Ovalcard.svg")
        obj.completed = false

      }
    },
    All() {
      this.state = 'all'
    },
    Active() {
      this.state = 'active'
    },
    Complete() {
      this.state = 'completed'
    },
    clearCompleted() {
      this.List = this.List.filter((arg) => !arg.completed)
    }
  },
  computed: {
    pusher() {
      let nun = this.List.length
      this.List.push({ value: this.text, index: nun + 1, image: require("@/assets/Ovalcard.svg"), completed: false })
      this.text = ""
      console.log(this.List)
    },
    filterList() {
      const act = { all: this.List, active: this.List.filter((arg) => !arg.completed), completed: this.List.filter((args) => args.completed) }
      return act[this.state]

    },
    activeList() {
      return this.List.filter((arg) => !arg.completed)
    },


  }
}
</script>
<style scoped>
.top {
  /* width: 100%; */
  height: 300px;
  background-image: url("@/assets/bg-desktop-dark.jpg");
  background-repeat: no-repeat;
}

.wrapper {
  position: absolute;
  width: 540px;
  /* height: 439px; */
  left: 450px;
  top: 246px;
  border-radius: 5px;
  border: 1px solid #25273D;
}

h6:hover,
h5:hover {
  cursor: pointer;
}

#hr {
  background-color: #393A4B;
  height: 3px;
  border: none;
  /* width: 98%; */
  margin-left: auto;
  margin-right: auto;
}

.unsho {
  display: none;
}

.bottom {
  /* width: 100%; */
  height: 700px;
  background-color: rgb(8, 8, 8);
}

.topic {
  display: flex;
  align-items: center;
  /* justify-content: space-evenly; */
  gap: 348px;
  padding-top: 70px;
  margin-left: 450px;
}

#comm {
  display: flex;
  gap: 19px;
}

.input {
  position: absolute;
  width: 540px;
  height: 64px;
  left: 450px;
  top: 158px;
}

h1 {
  width: 167px;
  height: 40px;
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 40px;
  letter-spacing: 15px;
  color: #FFFFFF;
}

#list_input {
  width: 540px;
  height: 64px;
  left: 450px;
  top: 158px;
  border: none;
  background: #25273D;
  box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
  border-radius: 5px;
  padding-left: 72px;
}

#list_input::placeholder {
  height: 18px;
  left: 23.53%;
  right: 0%;
  top: calc(50% - 18px/2);
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 18px;
  letter-spacing: -0.25px;
  color: #767992;
}

.butt {
  position: absolute;
  /* left: 0%; */
  right: 492px;
  top: 20px;
  background: #25273D;
  border-radius: 100%;
  border: none;
  /* border: 1px solid #393A4B; */
}

.unshow {
  display: none;
}

.unshow2,
.unshow1 {
  display: block;
}

.show2,
.show1 {
  display: none;
}

.lister {
  display: flex;
  /* flex-direction: column-reverse; */
  justify-content: space-between;
  align-items: center;
  gap: 56px;
  width: 540px;
  height: 64px;
  border: none;
  background: #25273D;
  box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
  padding-left: 24px;
  padding-right: 24px;
}

.blue {
  color: hsla(220, 98%, 61%, 1);

}

#coma {
  display: none;
}

.list {
  width: 540px;
  height: 64px;
  border: none;
  background: #25273D;
  box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
  /* border-radius: 5px; */
  padding-left: 24px;
  padding-right: 24px;
  display: flex;
  flex-direction: row-reverse;
  align-items: center;
  justify-content: left;
  gap: 24px;
}


.butto {
  background: #25273D;
  border-radius: 100%;
  border: none;
}

.textList h2 {
  height: 18px;
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 18px;
  letter-spacing: -0.25px;
  color: #C8CBE7;
}

@media screen and (max-width: 375px) {
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .bottom {
    height: 612px;
  }

  .top {
    height: 200px;
  }

  .input {
    width: 327px;
    height: 48px;
    left: 24px;
    top: 108px;
  }

  #list_input {
    width: 327px;
    height: 48px;
    left: 24px;
    top: 108px;

    background: #25273D;
    box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
    border-radius: 5px;
  }

  .wrapper {
    width: 327px;
    border: none;
    left: 24px;
    top: 172px;
  }

  #comm {
    display: none;
  }

  .lister,
  .list {
    width: 327px;
    height: 48px;
  }

  #coma {
    position: relative;
    width: 327px;
    height: 48px;
    top: 10px;
    left: 0px;
    border: none;
    background: #25273D;
    box-shadow: 0px 35px 50px -15px rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    gap: 18px;
    border-radius: 5px;
    align-items: center;
  }

  h4 {
    height: 12px;
    font-family: 'Josefin Sans';
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 12px;
    letter-spacing: -0.166667px;
    color: #5B5E7E;
  }

  .textList {
    height: 12px;
    left: 11.15%;
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 12px;
    letter-spacing: -0.166667px;
    color: #C8CBE7;
  }

  #list_input::placeholder {
    height: 12px;
    font-size: 12px;
    line-height: 12px;
    letter-spacing: -0.166667px;
  }

  h5 {
    height: 12px;
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 12px;
    text-align: right;
    letter-spacing: -0.166667px;
    color: #5B5E7E;
  }

  h6 {
    height: 14px;
    font-style: normal;
    font-weight: 700;
    font-size: 14px;
    line-height: 14px;
    letter-spacing: -0.194444px;
    color: #5B5E7E;
  }

  .topic {
    margin-left: 0;
    gap: 196px;
    justify-content: center;
    padding-top: 48px;
  }

  h1 {
    width: 108px;
    height: 20px;
    font-style: normal;
    font-weight: 700;
    font-size: 20px;
    line-height: 20px;
    letter-spacing: 10px;
  }

  #list_input {
    padding-left: 40px;
  }

}
</style>
