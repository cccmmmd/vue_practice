<template>
    <h1>Computed</h1>
    <div>
        <h3>輸入個別組成 Full name</h3>
        <input type="text" v-model="firstname">
        <input type="text" v-model="lastname">
        <p>Full Name:{{fullName}}</p>
        <br/>
        <h3>輸入 Full name 拆成個</h3>
        <input type="text" v-model="fullName">
        <p>Fist Name:{{firstname}}</p>
        <p>Last Name: {{lastname}}</p>
    </div>
    <div>
        <h3>輸入小數輸出百分比</h3>
        <input text="number" v-model="num" name="num"></input>  {{ numFun }}
    </div>
    
    <h3>for 迴圈</h3>
    <p v-for="(value, key, index) in dataList" :key="key">
        {{index}}:{{key}}{{value}}
    </p>
    <h3>v-if, v-if-else, v-else</h3>
    <button @click="changeView(1)">顯示單向綁定</button>
    <button @click="changeView(2)">顯示雙向綁定</button>
    <button @click="changeView(100)">沒畫面</button>
    <div class="sec1" v-if="view === 1">
        <p>單向綁定</p>
        <p>{{test}}</p>
    </div>
    <div class="sec1" v-else-if="view === 2">
        <p>雙向綁定</p>
        <input type="text" v-model = "inputtext" />
        <p>{{inputtext}}</p>
    </div>
    <div v-else>
        沒畫面
    </div>
    <button @click="changeView(3)">顯示單向綁定</button>
    <button @click="changeView(4)">顯示雙向綁定</button>
    <div class="sec1" v-show="view === 3">
        <p>單向綁定</p>
        <p>{{test}}</p>
    </div>
    <div class="sec1" v-show="view === 4">
        <p>雙向綁定</p>
        <input type="text" v-model = "inputtext" />
        <p>{{inputtext}}</p>
    </div>
    <div v-show="view !==3 && view !==4">
        沒畫面
    </div>
  
  
</template>
<script setup>
import {computed, ref} from 'vue'

    const test = 'AAA'
    const inputtext = ref("")

    const view = ref(1)
    const changeView = (index) => {
        view.value = index
    }
    
    const dataList = {
        k1:'a',
        k2:'b',
        k3:'c',
        k4:'d',
        k5:'e',
        k6:'f'
    }

    const num = ref(0)
    const numFun = computed(() => {
        if (Number.isNaN(num.value * 100)) return num.value
        return `${num.value * 100} %`
    })

    const firstname = ref('aaa')
    const lastname = ref('vv')
    const fullName = computed({
        get(){
            return `${firstname.value} ${lastname.value}`
        },
        set(newName){
            const [newfirstName, newlastName] = newName.split(' ')
            firstname.value = newfirstName
            lastname.value = newlastName
        }
    })
</script>
<style scoped>

</style>
