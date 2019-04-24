# org-tree
组加架构展示图
效果图如下：
![Image text](https://raw.githubusercontent.com/krifyFan/image-folder/master/2019-04-22_165646.png)

使用方法<br>
1、在parent.vue中引入组织架构组件org-tree.vue，org-tree.vue接收父组件的传值data<br>

设计原理<br>
1、用到了vue的递归组件，因为每个节点都应该是相同的组件<br>
2、 在官网这句话就是关键定义组件是一定要有name属性。<br>
    组件在它的模板内可以递归地调用自己，只有当它有 name 选项时才可以。<br>
```javascript
<template>
    <div class="org-tree-container">
        <div class="org-tree-node" v-for="item in data" :key="item.id">
            <div class="org-tree-node-label">
                <slot>
                    <div class="org-tree-label-name">{{item.name}}</div>
                </slot>
            </div>
            <div class="org-tree-add" v-if="item.children"></div>
            <div class="org-tree-node-children" v-if="item.children">
                <org-tree-node :data="item.children"></org-tree-node>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'orgTreeNode' //这个name一定要有
}
```
3、css
节点与节点之间的连线，充分利用了伪类::before ::after
