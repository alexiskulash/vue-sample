<script setup>
defineProps({
  type: {
    type: String,
    default: "button",
  },
  variant: {
    type: String,
    default: "primary",
    validator: (value) => ["primary", "secondary", "outline"].includes(value),
  },
  size: {
    type: String,
    default: "medium",
    validator: (value) => ["small", "medium", "large"].includes(value),
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});

defineEmits(["click"]);
</script>

<template>
  <button
    :type="type"
    :disabled="disabled"
    :class="[
      'base-button',
      `base-button--${variant}`,
      `base-button--${size}`,
      { 'base-button--disabled': disabled },
    ]"
    @click="$emit('click', $event)"
  >
    <slot />
  </button>
</template>

<style scoped>
.base-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: inherit;
  font-weight: 600;
  text-decoration: none;
  border: 2px solid transparent;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  white-space: nowrap;
  user-select: none;
}

.base-button:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.25);
}

/* Size variants */
.base-button--small {
  padding: 8px 16px;
  font-size: 14px;
  line-height: 1.2;
}

.base-button--medium {
  padding: 12px 24px;
  font-size: 16px;
  line-height: 1.2;
}

.base-button--large {
  padding: 16px 32px;
  font-size: 18px;
  line-height: 1.2;
}

/* Primary variant */
.base-button--primary {
  background-color: #007bff;
  color: white;
  border-color: #007bff;
}

.base-button--primary:hover:not(:disabled) {
  background-color: #0056b3;
  border-color: #0056b3;
  transform: translateY(-1px);
}

.base-button--primary:active {
  transform: translateY(0);
}

/* Secondary variant */
.base-button--secondary {
  background-color: #6c757d;
  color: white;
  border-color: #6c757d;
}

.base-button--secondary:hover:not(:disabled) {
  background-color: #545b62;
  border-color: #545b62;
  transform: translateY(-1px);
}

.base-button--secondary:active {
  transform: translateY(0);
}

/* Outline variant */
.base-button--outline {
  background-color: transparent;
  color: #007bff;
  border-color: #007bff;
}

.base-button--outline:hover:not(:disabled) {
  background-color: #007bff;
  color: white;
  transform: translateY(-1px);
}

.base-button--outline:active {
  transform: translateY(0);
}

/* Disabled state */
.base-button--disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none !important;
}

.base-button--disabled:hover {
  transform: none;
}
</style>
