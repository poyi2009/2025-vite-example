<script setup>
import { ref } from 'vue'
const drinks = ref([
  {
    id: 1,
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20,
    edit: false,
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18,
    edit: false,
  },
  {
    id: 3,
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34,
    edit: false,
  },
  {
    id: 4,
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10,
    edit: false,
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25,
    edit: false,
  },
  {
    id: 6,
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20,
    edit: false,
  },
  {
    id: 7,
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18,
    edit: false,
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20,
    edit: false,
  },
])
function reduceNum(drink) {
  if (drink.stock > 0) {
    drink.stock -= 1
  }
}
function addNum(drink) {
  drink.stock += 1
}
function startEdit(drink) {
  drink.edit = true
}
function endEdit(drink) {
  drink.edit = false
}
</script>

<template>
  <div class="wrap">
    <div>
      <h2>WEEK 1 : 餐點管理工具</h2>
      <table>
        <thead>
          <tr>
            <th scope="col">品項</th>
            <th scope="col">描述</th>
            <th scope="col">價格</th>
            <th scope="col">庫存</th>
            <th scope="col">操作</th>
            <th scope="col"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="drink in drinks" :key="drink.id">
            <td>
              {{ drink.name }}
            </td>
            <td>
              {{ drink.description }}
            </td>
            <td>{{ drink.price }} 元</td>
            <td class="stock">
              <button v-on:click="reduceNum(drink)">-</button>
              {{ drink.stock }}
              <button v-on:click="addNum(drink)">+</button>
            </td>
            <td v-if="drink.edit">
              <button v-on:click="endEdit(drink)" style="color: green">確認</button>
            </td>
            <td v-else>
              <button v-on:click="startEdit(drink)">編輯</button>
            </td>
            <td v-if="drink.edit">
              <input type="text" v-model="drink.name" />
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;700&display=swap');
.wrap {
  font-family: 'Oswald';
  display: flex;
  flex-direction: column;
}
table {
  text-align: center;
  font-size: 18px;
}
th,
td {
  padding: 8px 10px;
}
.stock {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
button {
  cursor: pointer;
  margin-left: 10px;
  margin-right: 10px;
  background-color: white;
  border: 1px solid rgb(134, 134, 134);
  border-radius: 0.5rem;
  width: 50px;
  height: 50px;
}
input {
  height: 30px;
  font-size: 18px;
}
</style>
