<template>
  <div class="table-box">
    <div class="table-box-content">
      <div class="cus-table" :style="{ width: scroll.x > 0 ? scroll.x + 'px' : 'auto', height: scroll.y > 0 ? scroll.y + 'px' : 'auto' }">
        <div class="table-header">
          <div v-for="(item, index) in columns" :key="index" class="header-item" :class="{'right-line': index < columns.length - 1, 'fixed-sticky': item.fixed }">
            <div class="header-top-item">
              {{ item.title }}
              <span v-if="item.unit">({{ item.unit }})</span>
            </div>
            <div v-if="item.children" class="header-bottom-item">
              <div v-for="(childItem, childIndex) in item.children" :key="childIndex" class="header-bottom-item-child" :class="{'left-line': childIndex > 0}">
                {{ childItem.title }}
              </div>
            </div>
          </div>
        </div>
        <div class="top-line">
          <div v-for="(contentItem, contentIndex) in tableData" :key="contentIndex" class="content-item-box" :class="{'top-line': contentIndex > 0}">
            <div v-for="(item, index) in columns" :key="index" class="content-item" :class="{'right-line': index < columns.length - 1, 'fixed-sticky': item.fixed}">
              <div v-if="item.children" class="content-item-child-box">
                <div v-for="(childItem, childIndex) in item.children" :key="childIndex" class="child-item" :class="{'left-line': childIndex > 0}">
                  {{ contentItem[item.key][childItem.key] || '' }}
                </div>
              </div>
              <div v-else>{{ contentItem[item.key] || '' }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>


defineProps({
  columns: {
    type: Array,
    default: () => []
  },
  tableData: {
    type: Array,
    default: () => []
  },
  scroll: {
    type: { x: Number, y: Number },
    default: () => {
      return {
        x: 0,
        y: 0
      }
    }
  }
})




</script>

<style lang="less" scoped>
  @line-color: #999;
  .table-box {
    border-radius: 8px;
    border: 1px solid @line-color;
    width: 100%;
    overflow: hidden;
    .table-box-content {
      overflow: scroll;
      position: relative;
    }
  }
  .cus-table {
    .table-header {
      display: flex;

      .header-item {
        flex: 1;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background-color: #fff;
        box-sizing: border-box;

        .header-top-item {
          display: flex;
          flex-direction: column;
          align-items: center;
        }
        .header-bottom-item {
          width: 100%;
          display: flex;
          border-top: 1px solid @line-color;

          .header-bottom-item-child {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
          }
        }
      }
    }

    .content-item-box {
      display: flex;
      .content-item {
        flex: 1;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: #fff;
        box-sizing: border-box;
      }
      .content-item-child-box {
        width: 100%;
        display: flex;
        .child-item {
          flex: 1;
          display: flex;
          justify-content: center;
          align-items: center;
        }
      }
    }

    .top-line {
      border-top: 1px solid @line-color;
    }

    .left-line {
      border-left: 1px solid @line-color;
    }
    .right-line {
      border-right: 1px solid @line-color;
    }
    .fixed-sticky {
      position: sticky;
      left: 0;
    }
  }
</style>