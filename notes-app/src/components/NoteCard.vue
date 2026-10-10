<template>
  <div class="note-card">
    <h3>{{ title }}</h3>
    <p>{{ message }}</p>
    <p>{{ message.toUpperCase() }}</p>
    <p>{{ 1 + 2 * 3 }}</p>
    <p>count = {{ count }}(三秒后自动变100)</p>
    <p v-text="rawtext"></p>
    <p v-html="htmltext"></p>
    <img :src="imgSrc" :title="tipTitle" width="96" alt="vue logo" />
    <p :class="{ active: count > 0 }">我是受 class 绑定控制的文字</p>
    <p :class="{ active: count > 0 }">我是受 class 绑定控制的文字</p>
     <button @click="count++">count +1（内联语句）</button>
    <button @click="say('你好', $event)">say（方法 + 传参）</button>
    <p>实时展示 → 姓名:{{ form.name }}｜性别:{{ form.gender }}｜爱好:{{ form.hobbies.join('、') }}</p>

    <input v-model="form.name" placeholder="输入姓名" />
    <label><input type="radio" value="男" v-model="form.gender" /> 男</label>
    <label><input type="radio" value="女" v-model="form.gender" /> 女</label>
    <label><input type="checkbox" value="篮球" v-model="form.hobbies" /> 篮球</label>
    <label><input type="checkbox" value="编程" v-model="form.hobbies" /> 编程</label>
        <button @click="show = !show">切换显隐（观察 DevTools 元素面板）</button>
    <p v-if="show">v-if：条件为真我才被"渲染"出来</p>
    <p v-else>v-else：上面条件为假时才轮到我</p>
    <p v-show="show">v-show：我一直存在，只是被 display:none 藏起来</p>
        <ul>
      <li v-for="(subject, index) in subjects" :key="index">
        {{ index }} - {{ subject }}
      </li>
    </ul>
    <button @click="subjects[1] = '英语（索引赋值）'">数组索引赋值</button>
<button @click="form.school = '成都理工大学工程技术学院'">对象新增属性</button>
<p v-if="form.school">{{ form.school }}</p>
  </div>
</template>

<script>
import vueLogo from '../assets/vue.svg'
export default {
  name: 'NoteCard',
  data() {
    return {
      title: '我的第一条笔记',
      message: 'hello vue',
      count: 0,
      rawtext: '<b>我是v-text的纯文本</b>',
      htmltext: '<b>我是html解析出的加粗</b>',
            imgSrc: vueLogo,
      tipTitle: '这是鼠标悬停提示',
            form: { name: '', gender: '', hobbies: [] },
                  show: true,
                        subjects: ['语文', '数学', 'Vue'],
    }
  },
    methods: {
    say(word, event) {
      alert(word + '｜事件类型：' + event.type)
    },
  },
  mounted() {
    setTimeout(() => {
      this.count = 100
    }, 3000)
  },
}
</script>

<style scoped>
.note-card {
  border: 1px solid #42b883;
  padding: 10px 16px;
  border-radius: 6px;
}.active {
    color: #42b883;
    font-weight: bold;
  }

</style>
