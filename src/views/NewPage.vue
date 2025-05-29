<script setup>
import { ref } from "vue";
import BaseButton from "../components/BaseButton.vue";

const clickCount = ref(0);
const message = ref("");

const handleButtonClick = (buttonType) => {
  clickCount.value++;
  message.value = `You clicked the ${buttonType} button! (${clickCount.value} total clicks)`;
};

const resetCounter = () => {
  clickCount.value = 0;
  message.value = "Counter reset!";
};
</script>

<template>
  <div class="new-page">
    <header class="page-header">
      <h1 class="page-title">New Page with Button Components</h1>
      <p class="page-description">
        This page demonstrates the usage of our custom BaseButton component with
        different variants and sizes.
      </p>
    </header>

    <main class="page-content">
      <section class="button-showcase">
        <h2 class="section-title">Button Variants</h2>

        <div class="button-group">
          <h3 class="group-title">Primary Buttons</h3>
          <div class="buttons-row">
            <BaseButton
              variant="primary"
              size="small"
              @click="handleButtonClick('small primary')"
            >
              Small Primary
            </BaseButton>
            <BaseButton
              variant="primary"
              size="medium"
              @click="handleButtonClick('medium primary')"
            >
              Medium Primary
            </BaseButton>
            <BaseButton
              variant="primary"
              size="large"
              @click="handleButtonClick('large primary')"
            >
              Large Primary
            </BaseButton>
          </div>
        </div>

        <div class="button-group">
          <h3 class="group-title">Secondary Buttons</h3>
          <div class="buttons-row">
            <BaseButton
              variant="secondary"
              size="small"
              @click="handleButtonClick('small secondary')"
            >
              Small Secondary
            </BaseButton>
            <BaseButton
              variant="secondary"
              size="medium"
              @click="handleButtonClick('medium secondary')"
            >
              Medium Secondary
            </BaseButton>
            <BaseButton
              variant="secondary"
              size="large"
              @click="handleButtonClick('large secondary')"
            >
              Large Secondary
            </BaseButton>
          </div>
        </div>

        <div class="button-group">
          <h3 class="group-title">Outline Buttons</h3>
          <div class="buttons-row">
            <BaseButton
              variant="outline"
              size="small"
              @click="handleButtonClick('small outline')"
            >
              Small Outline
            </BaseButton>
            <BaseButton
              variant="outline"
              size="medium"
              @click="handleButtonClick('medium outline')"
            >
              Medium Outline
            </BaseButton>
            <BaseButton
              variant="outline"
              size="large"
              @click="handleButtonClick('large outline')"
            >
              Large Outline
            </BaseButton>
          </div>
        </div>

        <div class="button-group">
          <h3 class="group-title">Disabled State</h3>
          <div class="buttons-row">
            <BaseButton variant="primary" disabled>
              Disabled Primary
            </BaseButton>
            <BaseButton variant="secondary" disabled>
              Disabled Secondary
            </BaseButton>
            <BaseButton variant="outline" disabled>
              Disabled Outline
            </BaseButton>
          </div>
        </div>
      </section>

      <section class="interaction-demo">
        <h2 class="section-title">Interactive Demo</h2>
        <div class="demo-area">
          <div class="demo-controls">
            <BaseButton variant="primary" @click="handleButtonClick('demo')">
              Click Me!
            </BaseButton>
            <BaseButton variant="outline" @click="resetCounter">
              Reset Counter
            </BaseButton>
          </div>

          <div class="demo-feedback">
            <p class="click-counter">Total Clicks: {{ clickCount }}</p>
            <p class="message" v-if="message">{{ message }}</p>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
.new-page {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
  font-family: inherit;
}

.page-header {
  text-align: center;
  margin-bottom: 3rem;
}

.page-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.page-description {
  font-size: 1.2rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.page-content {
  display: flex;
  flex-direction: column;
  gap: 3rem;
}

.section-title {
  font-size: 2rem;
  font-weight: 600;
  color: #2c3e50;
  margin-bottom: 2rem;
  text-align: center;
}

.button-showcase {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.button-group {
  background: #f8f9fa;
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid #e9ecef;
}

.group-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: #495057;
  margin-bottom: 1.5rem;
  text-align: center;
}

.buttons-row {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  flex-wrap: wrap;
}

.interaction-demo {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  padding: 3rem;
  border-radius: 16px;
  color: white;
  text-align: center;
}

.interaction-demo .section-title {
  color: white;
  margin-bottom: 2rem;
}

.demo-area {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
}

.demo-controls {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

.demo-feedback {
  background: rgba(255, 255, 255, 0.1);
  padding: 1.5rem;
  border-radius: 8px;
  backdrop-filter: blur(10px);
  min-height: 80px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-width: 300px;
}

.click-counter {
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.message {
  font-size: 1rem;
  opacity: 0.9;
  font-style: italic;
}

/* Responsive design */
@media (max-width: 768px) {
  .new-page {
    padding: 1rem;
  }

  .page-title {
    font-size: 2rem;
  }

  .page-description {
    font-size: 1rem;
  }

  .button-group {
    padding: 1.5rem;
  }

  .buttons-row {
    flex-direction: column;
    align-items: stretch;
  }

  .demo-controls {
    flex-direction: column;
    width: 100%;
  }

  .demo-feedback {
    min-width: auto;
    width: 100%;
  }
}

@media (max-width: 480px) {
  .page-title {
    font-size: 1.75rem;
  }

  .section-title {
    font-size: 1.5rem;
  }

  .group-title {
    font-size: 1.25rem;
  }

  .interaction-demo {
    padding: 2rem 1rem;
  }
}
</style>
