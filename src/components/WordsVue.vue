<template>
  <div id="words">
    <b-row no-gutters="ture">
      <b-col cols="3" id="nav">
      <div v-for="(item, index) in items"  
      :key="item.id" 
      :class="{'active': current==index, 'nav-item':true}" 
      @click="select_item(item, index)">
      {{item.text}}
      </div>
      </b-col>
      <b-col cols="9">
        <div class="content">
          <router-view></router-view>
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import router from '@/router'
export default {
  data() {
    return {
      current: 0,
      items:[ 
        {
          id:1,
          text:'概览',
          url:'/myword/tot'
        },
        {
          id:2,
          text:'单词添加',
          url:'/myword/add'
        },
          {
            id:3,
          text:'单词测试',
          url:'/myword/test'
        },
          {
            id:4,
          text:'过去式/分词',
          url:'/myword/add'
        },
          {
            id:5,
          text:'比较/最高级',
          url:'/myword/compare'
        },
      ]
    };
  },
  methods:{
    select_item(item, index){
      this.current = index
      router.push(item.url)
    }
  },
  mounted(){
    if(!this.current)
      router.push(this.items[0].url)
  }
};
</script>

<style scoped>
#nav {
  margin-top: 30px;
  /* border: solid 1px; */
  /* border-radius: 1px; */
  padding: auto;
}
.nav-item  {
  display: flex;
  text-align: center;
  vertical-align: middle;
  border-bottom: solid 1px;
  height: 50px;
  justify-content: center;
  align-items: center;
  color:gray;
  font-weight: 600;
}

.active {
  color: black;
}
</style>