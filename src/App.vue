<script setup>
import { ref } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
import NewPage from "./views/NewPage.vue";

const currentView = ref("welcome"); // 'welcome' or 'newpage'

const showWelcome = () => {
  currentView.value = "welcome";
};

const showNewPage = () => {
  currentView.value = "newpage";
};
</script>

<template>
  <div class="app">
    <nav class="navigation">
      <img
        alt="Vue logo"
        class="logo"
        src="./assets/logo.svg"
        width="60"
        height="60"
      />
      <div class="nav-links">
        <button
          @click="showWelcome"
          :class="['nav-button', { active: currentView === 'welcome' }]"
        >
          Welcome
        </button>
        <button
          @click="showNewPage"
          :class="['nav-button', { active: currentView === 'newpage' }]"
        >
          New Page
        </button>
      </div>
    </nav>

    <main class="main-content">
      <div v-if="currentView === 'welcome'" class="view">
        <header class="welcome-header">
          <div class="wrapper">
            <HelloWorld msg="You did it!" />
          </div>
        </header>
        <TheWelcome />
      </div>

      <div v-if="currentView === 'newpage'" class="view">
        <NewPage />
      </div>
    </main>
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.navigation {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
  background: #fff;
  border-bottom: 1px solid #e9ecef;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.logo {
  display: block;
  transition: transform 0.2s ease;
}

.logo:hover {
  transform: scale(1.1);
}

.nav-links {
  display: flex;
  gap: 1rem;
}

.nav-button {
  padding: 0.75rem 1.5rem;
  background: transparent;
  border: 2px solid #007bff;
  border-radius: 8px;
  color: #007bff;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.2s ease;
}

.nav-button:hover {
  background: #007bff;
  color: white;
  transform: translateY(-1px);
}

.nav-button.active {
  background: #007bff;
  color: white;
}

.main-content {
  flex: 1;
  overflow-x: hidden;
}

.view {
  animation: fadeIn 0.3s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.welcome-header {
  line-height: 1.5;
  padding: 2rem;
  text-align: center;
}

.wrapper {
  max-width: 1200px;
  margin: 0 auto;
}

@media (max-width: 768px) {
  .navigation {
    padding: 1rem;
    flex-direction: column;
    gap: 1rem;
  }

  .nav-links {
    width: 100%;
    justify-content: center;
  }

  .nav-button {
    flex: 1;
    max-width: 150px;
  }

  .welcome-header {
    padding: 1rem;
  }
}
</style>
