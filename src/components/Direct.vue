<template>
  <div class="direct">
    <div class="inner">
      <ul>
        <li 
          v-for="item in directs"
          :key="item.name">
          <a :href="item.href">
            <div>
              <img 
                :src="item.src" 
                :alt="item.name"
                width="90">
              <div class="text">
                {{item.name}}
              </div>
            </div>
          </a>
        </li>
        <li>
          <div 
            class="open-more"
            @click="onNav('LNB')">
            <div class="icon"></div>
            <div class="text">
              더보기
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      directs: []
    }
  },
  created(){
    this.init()
  },
  methods: {
    async init(){
      this.directs = await this.$fetch({
        requestName:'directs'
      })
    },
    onNav(name){
      this.$store.dispatch('navigations/onNav', name)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>