<template>
  <div :class="['sidebar', { collapsed }]">
    <div class="sidebar-title">
      <h1 v-if="!collapsed">Finance</h1>
      <i class="fas fa-bars" @click="toggleCollapse"></i>
    </div>
    <ul>
      <li
        v-for="(item, index) in menuItems"
        :key="index"
        :class="getItemClasses(item)"
        @click="setActive(item.name)"
      >
        <i :class="item.icon"></i>
        <span v-if="!collapsed">{{ item.label }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  data() {
    return {
      activeItem: "dashboard",
      collapsed: false,
      menuItems: [
        { name: "dashboard", label: "Dashboard", icon: "far fa-chart-bar" },
        {
          name: "transactions",
          label: "Transactions",
          icon: "fas fa-money-bill-alt",
        },
        { name: "accounts", label: "Accounts", icon: "far fa-credit-card" },
        { name: "budgets", label: "Budgets", icon: "fa fa-calculator" },
        {
          name: "investments",
          label: "Investments",
          icon: "fas fa-chart-line",
        },
        { name: "taxes", label: "Taxes", icon: "fas fa-money-check-alt" },
        { name: "reports", label: "Reports", icon: "far fa-file" },
        { name: "settings", label: "Settings", icon: "far fa-save" },
        { name: "logout", label: "Logout", icon: "fas fa-sign-out-alt" },
      ],
    };
  },
  methods: {
    setActive(item) {
      this.activeItem = item;
    },
    toggleCollapse() {
      this.collapsed = !this.collapsed;
    },
    getItemClasses(item) {
      return {
        active: this.activeItem === item.name,
        "logout-item": item.name === "logout",
      };
    },
  },
};
</script>

<style scoped>
.sidebar {
  width: 260px;
  background-color: #274472;
  color: #fff;
  min-height: 100%;
  max-height: 100vh;
  padding-top: 20px;
  z-index: 10;
  font-size: 15px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  transition: width 0.3s ease;
  overflow-y: scroll;
  font-family: "Assistant";
}

.sidebar.collapsed {
  width: 80px;
  padding-top: 30px;
}

.sidebar-title {
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sidebar-title h1 {
  font-family: "Unica One", sans-serif;
  font-weight: 400;
  margin: 0;
  color: #fff;
}

.sidebar-title i {
  cursor: pointer;
  font-size: 20px;
}

.sidebar ul {
  list-style: none;
  padding: 0;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.sidebar ul li {
  padding: 15px 10px;
  cursor: pointer;
  margin: 2px 2px;
  display: flex;
  align-items: center;
}

.sidebar ul li.logout-item {
  margin-top: auto;
  margin-bottom: 10px;
}

.sidebar ul li:hover {
  background-color: #055c9d;
}

.sidebar ul li.logout-item:hover i {
  color: #ff4d4f;
}

.sidebar ul li.active {
  background: #055c9d;
  color: white;
}

.sidebar ul li i {
  margin-right: 10px;
  margin-left: 5px;
  font-size: 16px;
}

.sidebar ul li.active i {
  color: white;
}

.sidebar.collapsed ul li,
.sidebar.collapsed .sidebar-title {
  justify-content: center;
}

.sidebar.collapsed ul li i {
  margin: 0;
  padding: 5px;
  font-size: 18px;
}
</style>
