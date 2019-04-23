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
    name: 'orgTreeNode',
    components: {
        OrgTreeNode: {
            render,
            functional: true
        }
    },
    props: {
        data: {
            type: Object
        }
    }
}
</script>
<style lang="less">
ul li{
    list-style: none;
}
.org-tree-node:only-child::after,
.org-tree-node:only-child::before{
    display: none;
}
.org-tree-add{
    border: 1px solid #cccccc;
    width: 24px;
    height: 24px;
    color: #cccccc;
    -webkit-transition: all 0.2s;
    transition: all 0.2s;
    position: relative;
    border-radius: 20px;
    position: absolute;
    left: 52%;
    top: 100px;
    z-index: 999;
    margin-left: -12px;
    background: #fff;
}
.org-tree-add::before{
    content: ' ';
    position: absolute;
    left: 50%;
    top: 50%;
    width: 20px;
    margin-left: -10px;
    margin-top: -1px;
    border-top: 2px solid;
}
.org-tree-node-label .org-tree-label-name{
    box-shadow: 0 2px 5px 0 rgba(0,0,0,0.16), 0 2px 10px 0 rgba(0,0,0,0.12);
    display: inline-block;
    padding: 10px;
    margin: 0px;
    font-size: 16px;
}
.org-tree-node {
    padding-top: 30px;
    display: table-cell;
    vertical-align: top;
  
    &.is-leaf, &.collapsed {
        padding-left: 10px;
        padding-right: 10px;
    }
  
    &:before, &:after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 53%;
        height: 30px;
    }
  
    &:after {
        left: 53%;
        border-left: 1px solid #ddd;
    }
  
    &:not(:first-child):before,
    &:not(:last-child):after {
        border-top: 1px solid #ddd;
    }

  
}
.org-tree-container {
    display: inline-block;
    padding: 30px;
    background-color: #fff;
}
.org-tree-node-label {
    position: relative;
    display: inline-block;
    width: 100%;
    text-align: center;
    margin: 0 10px;

  
    .org-tree-node-label-inner {
      padding: 10px 15px;
      text-align: center;
      border-radius: 3px;
      box-shadow: 0 1px 5px rgba(0, 0, 0, .15);
    }
}
.org-tree-node,.org-tree-node-children {
    position: relative;
    margin: 0;
    list-style-type: none;
  
    &:before, &:after {
      transition: all .35s;
    }
}
.org-tree-node-children {
    padding-top: 6px;
    display: table;
  
    &:before {
        content: '';
        position: absolute;
        top: 0;
        left: 52%;
        width: 0;
        height: 37px;
        border-left: 1px solid #ddd;
    }
  
    &:after {
        content: '';
        display: table;
        clear: both;
    }
}
</style>
