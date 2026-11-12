<template>
  <CoreSideNavGroup
    v-bind="coreAttrs"
    :open="open"
    :disabled="disabled"
    :on-click="(event: MouseEvent) => emit('click', event)"
    :on-focus="(event: FocusEvent) => emit('focus', event)"
    :on-blur="(event: FocusEvent) => emit('blur', event)"
    :on-key-down="(event: KeyboardEvent) => emit('keydown', event)"
    :on-key-up="(event: KeyboardEvent) => emit('keyup', event)"
  >
    <template #label>
      <slot name="label" />
    </template>
    <template #actions>
      <slot name="actions" />
    </template>
    <slot />
  </CoreSideNavGroup>
</template>

<script setup lang="ts">
import CoreSideNavGroup from './atoms/sidenav/SideNavGroup.vue';
import { useCoreAttrs } from './attrs';

defineOptions({ inheritAttrs: false });

export type Props = {
  open?: boolean;
  disabled?: boolean;
};

defineProps<Props>();

const emit = defineEmits<{
  click: [event: MouseEvent];
  focus: [event: FocusEvent];
  blur: [event: FocusEvent];
  keydown: [event: KeyboardEvent];
  keyup: [event: KeyboardEvent];
}>();

const coreAttrs = useCoreAttrs();
</script>
