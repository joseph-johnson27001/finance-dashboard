<template>
  <div class="card">
    <div class="header">
      <div class="icon-container">
        <i :class="iconClass"></i>
      </div>
      <span class="kpi-name">{{ kpiName }}</span>
    </div>
    <div class="value">{{ value }}</div>
  </div>
</template>

<script>
export default {
  props: {
    iconClass: {
      type: String,
      required: true,
    },
    kpiName: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
.card {
  background: white;
  padding: 15px;
  border-radius: 5px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.header {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.icon-container {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(100, 150, 255, 0.1);
  width: 40px;
  height: 40px;
  border-radius: 4px;
  margin-right: 10px;
}

.icon-container i {
  font-size: 20px;
  color: #6498ff;
}

.kpi-name {
  font-size: 14px;
  font-weight: 500;
  color: #274472;
}

.value {
  font-size: 18px;
  font-weight: 400;
  color: #333;
}
</style>
