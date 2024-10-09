<template>
  <div class="overflow-x-auto w-full">
    <table class="table">
      <!-- head -->
      <thead>
        <tr>
          <th></th>
          <th>Project</th>
          <th>Tasks</th>
          <th>Progress</th>
        </tr>
      </thead>
      <tbody>
        <!-- row 2 -->
        <tr class="hover">
          <th>2</th>
          <td>Hart Hagerty</td>
          <td>Desktop Support Technician</td>
          <td>Purple</td>
        </tr>
      </tbody>
    </table>
  </div>

  <custom-modal :open="customModalOpen">
    <template #headerSlot>
      <h1 class="text-3xl">Title Modal</h1>
    </template>

    <template #bodySlot>
      <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Fuga odio natus veniam expedita?
      </p>
    </template>

    <template #actionsSlot>
      <div class="flex justify-end">
        <button class="btn mr-4" @click="customModalOpen = false">Close</button>
        <button class="btn btn-primary" @click="customModalOpen = false">Accept</button>
      </div>
    </template>
  </custom-modal>

  <input-modal
    :open="modalOpen"
    @close="modalOpen = false"
    @value="onNewValue"
    title="New project"
    subtitle="Give your project a unique name"
    placeholder="Enter the name of the project"
  />

  <fab-button position="bottom-right" @click="modalOpen = true">
    <add-circle />
  </fab-button>

  <fab-button position="bottom-left" @click="customModalOpen = true">
    <modal-icon />
  </fab-button>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import CustomModal from '@/modules/common/components/CustomModal.vue';
import InputModal from '@/modules/common/components/InputModal.vue';
import FabButton from '@/modules/common/components/FabButton.vue';
import AddCircle from '@/modules/common/icons/AddCircle.vue';
import ModalIcon from '@/modules/common/icons/ModalIcon.vue';

const modalOpen = ref(false);
const customModalOpen = ref(false);

const onNewValue = (projectName: string) => {
  console.log({ projectName });
};
</script>
