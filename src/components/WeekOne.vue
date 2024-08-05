<script setup>
import { ref } from 'vue';

const menu = ref([
  {
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20
  },
  {
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 18
  },
  {
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 34
  },
  {
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10
  },
  {
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25
  },
  {
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20
  },
  {
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18
  },
  {
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20
  }
]);

const increaseStock = (index) => {
  menu.value[index].stock++;
};

const decreaseStock = (index) => {
  menu.value[index].stock--;
};

const modifyName = (index) => {
  const newName = prompt(`
    原本的名稱：${menu.value[index].name}\n
    請輸入新的名稱：
    `);
  if (newName?.trim().length > 0) {
    menu.value[index].name = newName;
  } else {
    alert('請輸入有效的品項名稱');
  }
};
</script>

<template>
  <!--
  Level	說明
（原版）LV1	將菜單轉為資料格式
（原版）LV2	可以重新設定菜單的庫存數量
（原版挑戰）LV3	還能再去設定品項名稱
  -->
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="({ name, description, price, stock }, i) of menu" :key="i">
        <td>{{ name }}<button type="button" @click="modifyName(i)">✏️</button></td>
        <td>
          <small>{{ description }}</small>
        </td>
        <td>{{ price }}</td>
        <td>
          <button type="button" @click="increaseStock(i)">+</button>{{ stock
          }}<button type="button" @click="decreaseStock(i)">-</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
