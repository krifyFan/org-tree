<template>
    <div>
        <vueTree :data="data"></vueTree>
    </div>
</template>
<script>
import vueTree from './components/org-tree'
export default {
  components: {
    vueTree
  },
  data() {
    return{
      data: [{
        id: 1,
        name: '总经理',
        children: [
          { id: 2, name: '副总经理', children: [
            { id: 4, name: '财务部' },
            { id: 5, name: '市场部' }
          ] },
          { id: 3, name: '副总经理',children: [
            { id: 6, name: '研发部' },
            { id: 7, name: '工程部' }
          ]}
        ]
      }],
    }
  },
}
</script>


