<template>

  <h1>지니쥬얼리 카페 레시피</h1>
  <div>


    <div class="addIngridient-wrap">
      <input type="text" v-model="ingridient" @keyup.enter="addIngridient">
      <input type="submit" value="+" @click="addIngridient">
    </div>
    <div class="ingridinet-wrap">
      <div>
        <div class="circle espresso">
        </div>
        <p class="small">에스프레소</p>
      </div>

      <div>
        <div class="circle milk">
        </div>
        <p class="small">스팀 밀크</p>
      </div>

      <div>
        <div class="circle foam">
        </div>
        <p class="small">밀크폼</p>
      </div>

      <div>
        <div class="circle water">
        </div>
        <p class="small">물</p>
      </div>

      <div>
        <div class="circle vanila">
        </div>
        <p class="small">바닐라시럽</p>
      </div>


      <div v-for="(ingridient, index) in ingridients" v-bind:key="ingridient" class="small">
        <color-picker v-model="color" @change="change"></color-picker>
        {{ ingridient }}
        <button class="delteButton" @click="deleteIngridient(index)">X</button>
      </div>

    </div>


    <ul class="menu-list">
      <li @click="recipe_0 = true">
        <div>
          <div class="cup-wrap">
            <div class="cup-small doppio">
              <div class="handle"></div>
            </div>
          </div>
          <div class="text-wrap">
            <h4>{{ name[0] }}</h4>
            <p>에스프레소 더블샷</p>
          </div>
        </div>
      </li>

      <li @click="recipe_1 = true">
        <div>
          <div class="cup-wrap">
            <div class="cup americano">
              <div class="handle"></div>
            </div>
          </div>
          <div class="text-wrap">
            <h4>{{ name[1] }}</h4>
            <p>에스프레소 더블샷, 물</p>
          </div>
        </div>
      </li>

      <li @click="recipe_2 = true">
        <div>
          <div class="cup-wrap">
            <div class="cup cappuccino">
              <div class="handle"></div>
            </div>
          </div>
          <div class="text-wrap">
            <h4>{{ name[2] }}</h4>
            <p>에스프레소 더블샷, 스팀밀크, 밀크폼</p>
          </div>
        </div>
      </li>

      <li @click="recipe_3 = true">
        <div>
          <div class="cup-wrap">
            <div class="cup-long latte">
              <div class="handle"></div>
              <div class="bottom-handle"></div>
            </div>
          </div>
          <div class="text-wrap">
            <h4>{{ name[3] }}</h4>
            <p>에스프레소 원샷, 스팀밀크, 밀크폼</p>
          </div>
        </div>
      </li>

      <li @click="recipe4 = true">
        <div>
          <div class="cup-wrap">
            <div class="cup-long latte vanilalatte">
              <div class="handle"></div>
              <div class="bottom-handle"></div>
            </div>
          </div>
          <div class="text-wrap">
            <h4>{{ name[4] }}</h4>
            <p>에스프레소 원샷, 스팀밀크, 바닐라시럽</p>
          </div>
        </div>
      </li>

      <li @click="recipe5 = true">
        <div>
          <div class="cup-wrap">
            <div class="cup cappuccino">
              <div class="handle"></div>
            </div>
          </div>
          <h4>{{ name[5] }}</h4>
        </div>
      </li>
    </ul>

  </div>

  <div class="black-bg" v-if="recipe_0===true">
    <div class="recipe-page white-bg">
      <div class="close" @click="recipe_0 = false">X</div>
      <h5> {{ name[0] }} 레시피</h5>
      <div class="recipe-cup">
        <div class="shot espresso drop"></div>
        <div class="shot espresso drop-2"></div>
        <div class="cup-wrap">
          <div class="cup-small doppio">
            <div class="handle"></div>
          </div>
        </div>
      </div>

      <input type="text" v-model="menu_0">
      <input type="submit" value="추가" @click="addMenu">

      <ol>
        <li v-for="(menu_0, index) in menus_0" v-bind:key="menu_0">
          {{ menu_0 }}

          <button class="delteButton" @click="deleteMenu_0(index)">삭제</button>
        </li>
      </ol>
    </div>
  </div>

  <div class="black-bg" v-if="recipe_1===true">
    <div class="recipe-page white-bg">
      <div class="close" @click="recipe_1 = false">X</div>
      <h5> {{ name[1] }} 레시피</h5>
      <div class="recipe-cup">
        <div class="shot espresso drop"></div>
        <div class="shot espresso drop-2"></div>
        <div class="shot water drop-3"></div>
        <div class="cup-wrap">
          <div class="cup americano">
            <div class="handle"></div>
          </div>
        </div>
      </div>

      <input type="text" v-model="menu_1">
      <input type="submit" value="추가" @click="addMenu_1">

      <ol>
        <li v-for="(menu_1, index) in menus_1" v-bind:key="menu_1">
          {{ menu_1 }}

          <button class="delteButton" @click="deleteMenu_1(index)">삭제</button>
        </li>
      </ol>
    </div>
  </div>

  <div class="black-bg" v-if="recipe_2===true">
    <div class="recipe-page white-bg">
      <div class="close" @click="recipe_2 = false">X</div>
      <h5> {{ name[2] }} 레시피</h5>
      <div class="recipe-cup">
        <div class="shot espresso drop"></div>
        <div class="shot espresso drop-2"></div>
        <div class="shot foam drop-3"></div>
        <div class="cup-wrap">
          <div class="cup cappuccino">
            <div class="handle"></div>
          </div>
        </div>
      </div>

      <input type="text" v-model="menu_2">
      <input type="submit" value="추가" @click="addMenu_2">

      <ol>
        <li v-for="(menu_2, index) in menus_2" v-bind:key="menu_2">
          {{ menu_2 }}

          <button class="delteButton" @click="deleteMenu_2(index)">삭제</button>
        </li>
      </ol>
    </div>
  </div>

  <div class="black-bg" v-if="recipe_3===true">
    <div class="recipe-page white-bg">
      <div class="close" @click="recipe_3 = false">X</div>
      <h5> {{ name[3] }} 레시피</h5>
      <div class="recipe-cup">
        <div class="shot espresso drop"></div>
        <div class="shot espresso drop-2"></div>
        <div class="shot foam drop-3"></div>
        <div class="cup-wrap">
          <div class="cup cappuccino">
            <div class="handle"></div>
          </div>
        </div>
      </div>

      <input type="text" v-model="menu_3">
      <input type="submit" value="추가" @click="addMenu_3">

      <ol>
        <li v-for="(menu_3, index) in menus_3" v-bind:key="menu_3">
          {{ menu_3 }}
          <button class="delteButton" @click="deleteMenu_3(index)">삭제</button>
        </li>
      </ol>
    </div>
  </div>

</template>

<script>

  var circle = ''


  export default {
    name: 'App',
    data() {
      return {
        parentMessage: circle,
        ingridients: ['카라멜시럽', '시나몬가루'],
        recipe_0: false,
        recipe_1: false,
        recipe_2: false,
        recipe_3: false,
        name: ['에스프레소', '아메리카노', '카푸치노', '카페라떼', '바닐라라뗴', '카페모카', '카라멜마끼아또', '아포가토', '옛날커피', '초코라떼', '카페라떼'],
        menus_0: ['에스프레소 2샷'],
        menus_1: ['에스프레소 2샷', '물 한컵'],
        menus_2: ['에스프레소 2샷', '스팀밀크'],
        menus_3: ['물  500ml', '1샷'],
        menu_: '',

      }
    },
    methods: {

      addIngridient() {
        this.ingridients.push(this.ingridient)
        this.ingridient = '';

      },

      addMenu() {
        this.menus_0.push(this.menu_0)
        this.menu_0 = '';

      },
      addMenu_1() {
        this.menus_1.push(this.menu_1)
        this.menu_1 = '';

      },
      addMenu_2() {
        this.menus_2.push(this.menu_2)
        this.menu_2 = '';

      },

      addMenu_3() {
        this.menus_3.push(this.menu_3)
        this.menu_3 = '';

      },

      deleteIngridient(index) {
        this.ingridients.splice(index, 1)
      },


      deleteMenu_0(index) {
        this.menus_0.splice(index, 1)
      },

      deleteMenu_1(index) {
        this.menus_1.splice(index, 1)
      },

      deleteMenu_2(index) {
        this.menus_2.splice(index, 1)
      },

      deleteMenu_3(index) {
        this.menus_3.splice(index, 1)
      },
      changeBack() {
        var el = document.getElementById("specific")
        console.log(el)
        el.style.backgroundColor = this.colors.rgba
      }


    },

    components: {


    }

  }





</script>