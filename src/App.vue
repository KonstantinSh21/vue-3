<template>
  <!--  <img alt="Vue logo" src="./assets/logo.png" />-->
  <div class="main-wrapper">
    <h1>{{nameProj}}</h1>
    <p>Данное приложение помогает повлиять на свою жизнь в течение 30 дней</p>
    <div v-if="!isStartProj">
      <p>Для старта необходимо собраться и готовиться к преодолеваю себя</p>
      <p>И нажать на эту кнопку</p>
      <button @click="start">Старт</button>
    </div>


    <WrapperDay
    v-else
    :objectDate="nowObj"
    />
  </div>
</template>
<script>
import {ref, reactive} from 'vue'
import WrapperDay from "./components/WrapperDay.vue";

export default {
  components: {
    WrapperDay
  },
  setup(props) {
    const nameProj = ref('Константин Ш');
    const isStartProj = ref(false);
    const nowDate = ref(0);

    const mainArray = ref([
      {id: 0, day: 1, title: 'Проведи день с самим собой'},
      {id: 1, day: 2, title: 'День офлайн'},
      {id: 2, day: 3, title: 'Медитация 15 минут'},
      {id: 3, day: 4, title: 'Запиши все, что хочешь сделать в жизни'},
      {id: 4, day: 5, title: 'Почисти подписки в соц сетях'},
      {id: 5, day: 6, title: 'Говори да всем предложениям'},
      {id: 6, day: 7, title: 'Запиши все, что раздражает'},
      {id: 7, day: 8, title: 'День без нытья и жалоб'},
      {id: 8, day: 9, title: 'Запиши цели на год'},
      {id: 9, day: 10, title: 'Избавься от старых обид'},
    ])

    const start = () => {
      isStartProj.value = true;
      searchNowObj(nowDate)
    };

    const nowObj = reactive({});

    const searchNowObj = (nowDate, ) => {
      mainArray.value.forEach(item => {
        // debugger
        if (item.id === nowDate.value) {
          nowObj.value = item
          // console.log(nowObj.value)
        }
      })
    };

    return {
      nameProj,
      isStartProj,
      start,
      nowDate,
      nowObj,
      searchNowObj,
      mainArray,
    }


  }

}
</script>
<style>

* {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

.main-wrapper {
  background-color: #f1f1f1;
  width: 100%;
  height: 100%;
  padding: 60px 0;
}

.main-wrapper p{
  padding-top: 16px;
}

.main-wrapper button {
  color: #000;
  background-color: #fff;
  margin-top: 48px;
  border: 2px solid #008CBA;
  padding: 16px 24px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 16px;
}

.main-wrapper button:hover {
  background-color: #008CBA;
  color: #fff;
}
</style>
