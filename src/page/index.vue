<template>
  <div>
    <projectHeader></projectHeader>
    <div class="article_list">
      <!-- <ul>
        <li v-for="i in list">
          <time v-text="i.create_at"></time>
          <router-link :to="'/content/' + i.id">
            {{ i.title }}
          </router-link>
        </li>
      </ul> -->
        <div style="float:left;width:20%;border-right:1px solid gray;height:100%;">
        </div>
        <div style="float:left;width:80%;">
            <router-view></router-view>
        </div>
    </div>
    <projectFooter></projectFooter>
  </div>
</template>
<script>
import projectHeader from '../components/header.vue'
import projectFooter from '../components/footer.vue'
export default {
  components: { projectHeader, projectFooter },
  data () {
    return {
      list: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topics', null, r => {
        // console.log(r)
        this.list = r.data
      })
    }
  }
}
</script>

