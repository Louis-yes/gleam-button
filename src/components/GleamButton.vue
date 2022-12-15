<script setup lang="ts">
import { reactive } from "vue";
interface Props {
  icon?: boolean;
  iconOnly?: boolean;
  disabled?: boolean;
  badgeCount?: number;
}
const props = withDefaults(defineProps<Props>(), {
  icon: false,
  iconOnly: false,
  disabled: false,
  badgeCount: NaN,
});
const state = reactive({ active: false });
function setActive(active: boolean) {
  state.active = active;
}
</script>
<template>
  <div
    class="gleam-button"
    :class="{
      icon: icon || iconOnly,
      'icon-only': iconOnly,
      active: state.active,
      disabled: disabled,
      'has-badge': badgeCount > 0,
    }"
    @mousedown="setActive(true)"
    @mouseup="setActive(false)"
    :tabindex="disabled ? -1 : 0"
  >
    <span v-if="icon || iconOnly" class="icon">
      <svg
        width="12"
        height="12"
        viewBox="0 0 12 12"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M6 1V11M1 6H11"
          stroke-width="1.3"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </span>
    <span v-if="!iconOnly">Button</span>
    <span v-if="badgeCount > 0" class="badge">
      <span class="diamond">
        <svg
          width="12"
          height="12"
          viewBox="0 0 12 12"
          fill="inherit"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M5.1471 0.149931L5.22952 0.149961H6H6.77048L6.8529 0.149931C7.36977 0.149648 7.7567 0.149435 8.12051 0.255077C8.4411 0.348166 8.74121 0.50099 9.00505 0.705507C9.30447 0.937604 9.53189 1.25066 9.83567 1.66884L9.88411 1.7355L11.3492 3.74998L11.3614 3.76679L11.3614 3.76683L11.3615 3.76685C11.4892 3.94246 11.6052 4.1019 11.6928 4.24342C11.7875 4.39642 11.8738 4.56627 11.918 4.76901C11.9831 5.06747 11.9642 5.37815 11.8631 5.66644C11.7945 5.86228 11.6882 6.02036 11.5755 6.16068C11.4713 6.29049 11.3368 6.43462 11.1886 6.59339L11.1744 6.60858L7.64487 10.3902L7.62805 10.4083L7.62804 10.4083C7.43914 10.6107 7.27075 10.7911 7.11897 10.9286C6.95743 11.075 6.77023 11.2152 6.53146 11.2964C6.18685 11.4137 5.81314 11.4137 5.46853 11.2964C5.22977 11.2152 5.04257 11.075 4.88102 10.9286C4.72924 10.7911 4.56084 10.6107 4.37194 10.4083L4.37192 10.4082L4.35512 10.3902L0.825586 6.60858L0.811404 6.59339L0.811365 6.59335C0.663183 6.4346 0.528654 6.29048 0.424447 6.16068C0.311787 6.02036 0.205472 5.86228 0.136854 5.66644C0.0358417 5.37815 0.0168461 5.06747 0.0819834 4.76901C0.126231 4.56627 0.212496 4.39642 0.307221 4.24342C0.394847 4.10188 0.510828 3.94243 0.638579 3.76679L0.650805 3.74998L2.11588 1.7355L2.16433 1.66883C2.46811 1.25065 2.69552 0.937602 2.99494 0.705507C3.25879 0.50099 3.5589 0.348166 3.87949 0.255077C4.2433 0.149435 4.63023 0.149648 5.1471 0.149931ZM4.24199 1.50351C4.37351 1.46532 4.5212 1.45392 4.90452 1.45092L3.21414 4.54996H1.67646C1.68482 4.53846 1.69338 4.52668 1.70216 4.5146L3.16724 2.50012C3.54099 1.98621 3.6568 1.8373 3.79138 1.73298C3.92579 1.62879 4.07868 1.55093 4.24199 1.50351ZM1.89579 5.84996L4.44442 8.58063L3.18411 5.84996H1.89579ZM4.61589 5.84996L6 8.84886L7.38411 5.84996H4.61589ZM8.81589 5.84996L7.55558 8.58064L10.1042 5.84996H8.81589ZM10.3235 4.54996H8.78586L7.09547 1.45092C7.4788 1.45392 7.62649 1.46532 7.758 1.50351C7.92132 1.55093 8.07421 1.62879 8.20862 1.73298C8.3432 1.8373 8.459 1.98621 8.83276 2.50012L10.2978 4.5146C10.3066 4.52667 10.3152 4.53846 10.3235 4.54996ZM7.30504 4.54996H4.69495L6 2.15737L7.30504 4.54996Z"
            fill="inherit"
          />
        </svg>
      </span>
      <span>{{ badgeCount }}</span>
    </span>
  </div>
</template>
<style scoped>
.gleam-button {
  --primary: #33b679;
  --primary-60: rgba(51, 182, 121, 0.6);
  --hover: linear-gradient(0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)),
    var(--primary);
  --active: linear-gradient(0deg, rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)),
    var(--primary);
  --disabled: linear-gradient(
      0deg,
      rgba(255, 255, 255, 0.6),
      rgba(255, 255, 255, 0.6)
    ),
    var(--primary);
  --text-primary: #ffffff;
  --shadow: 0px 2px 4px rgba(10, 14, 20, 0.08);
  --corner: 8px;

  --white: #ffffff;
  --grey-200: #f7f8fa;
  --grey-300: #f0f2f5;
  --grey-400: #d7dae0;
  --grey-500: #9096a3;
  --grey-700: #626a7a;
  --grey-900: #0a0e14;

  --text-ghost: var(--grey-900);
  --text-ghost-disabled: var(--grey-500);
  --background-ghost: var(--white);
  --background-ghost-disabled: var(--grey-200);
  --icon-stroke-ghost: var(--grey-700);
  --icon-stroke-ghost-hover: var(--grey-900);
  --icon-stroke-ghost-active: var(--grey-900);
  --border-ghost: 1px solid var(--grey-400);
  --border-ghost-hover: 1px solid var(--grey-500);
  --border-ghost-active: 1px solid var(--grey-900);
  --border-ghost-disabled: 1px solid var(--grey-400);
}
.gleam-button {
  display: inline-flex;
  width: fit-content;
  margin: 5px;

  justify-content: center;
  align-items: center;
  gap: 12px;

  padding: 10px 20px;

  background: var(--primary);
  box-shadow: var(--shadow);
  border-radius: var(--corner);

  color: var(--text-primary);
  font-style: normal;
  font-weight: 500;
  font-size: 13px;
  line-height: 20px;

  cursor: pointer;
}
.gleam-button:hover {
  background: var(--hover);
}
.gleam-button.active {
  background: var(--active);
}
.gleam-button.disabled {
  background: var(--disabled);
}
.gleam-button:focus:not(.disabled) {
  outline: 1px solid var(--primary-60);
  outline-offset: 3px;
}
.gleam-button .icon {
  width: 20px;
  height: 20px;

  display: flex;
  justify-content: center;
  align-items: center;

  stroke: var(--text-primary);
}
.gleam-button.icon-only {
  padding: 10px;
}
.gleam-button.has-badge {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-right: 16px;
}
.gleam-button.has-badge.icon-only {
  padding: 8px 8px 8px 10px;
}

.gleam-button .badge {
  display: inline-flex;
  align-items: center;
  justify-content: space-between;
  gap: 4px;
  height: 24px;
  width: 44px;
  border-radius: 100px;
  background: rgba(255, 255, 255, 0.12);
  padding: 2px 8px;
  font-size: 12px;
}
.gleam-button .badge .diamond {
  width: 16px;
  height: 16px;
  fill: var(--white);
  display: inline-flex;
  justify-content: center;
  align-items: center;
}
.gleam-button.ghost {
  background-color: var(--background-ghost);
  border: var(--border-ghost);
  border-radius: var(--corner);
  box-shadow: none;

  color: var(--text-ghost);
}
.gleam-button.ghost.disabled {
  color: var(--text-ghost-disabled);
  background: var(--background-ghost-disabled);
  border: var(--border-ghost-disabled);
}
.gleam-button.ghost:hover:not(.disabled) {
  background: var(--background-ghost);
  border: var(--border-ghost-hover);
}
.gleam-button.ghost.active:not(.disabled) {
  border: var(--border-ghost-active);
}
.gleam-button.ghost .icon {
  stroke: var(--icon-stroke-ghost);
}
.gleam-button.ghost:hover:not(.disabled) .icon {
  stroke: var(--icon-stroke-ghost-hover);
}
.gleam-button.ghost .badge {
  background-color: var(--grey-300);
}
.gleam-button.ghost.disabled .badge {
  color: var(--grey-500);
}
.gleam-button.ghost .badge .diamond {
  fill: var(--grey-900);
}
.gleam-button.ghost.disabled .badge .diamond {
  fill: var(--grey-500);
}
</style>
