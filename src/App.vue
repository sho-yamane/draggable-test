<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <draggable
            v-model="myArrays"
            group="people"
            @start="drag=true"
            @end="drag=false"
            tag="table"
            handle=".handle"
            draggable=".handle"
    >
      <template v-for="adviceGroup in myArrays">
        <tbody><tr><td>{{ adviceGroup.title }}</td></tr></tbody>
        <tbody v-for="advice in adviceGroup.advices" :key="`${adviceGroup.id}-${advice.id}`" class="handle">
          <tr>
            <td>{{advice.title}}</td>
          </tr>
        </tbody>
      </template>
    </draggable>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'app',
  components: {
    draggable
  },
  data() {
    return {
      myArrays: [
        {id: 1, title: 'カテゴリ1', advices: [{id: 1, title: 'item1'}, {id: 2, title: 'item2'}]},
        {id: 2, title: 'カテゴリ2', advices: [{id: 1, title: 'item3'}, {id: 2, title: 'item4'}]},
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.box {
  padding: 16px 24px;
  border: 1px solid #eaeaea;
  max-width: 500px;
}
</style>
