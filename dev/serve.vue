<template>
  <div id="app" class="darks">
    <div
      class="bg-white dark:bg-gray-900 max-w-screen-2xl h-screen mx-auto flex items-stretch overflow-y-auto"
    >
      <div class="mt-10 w-full">
        <div
          class="max-w-lg mx-auto px-6 py-5 bg-white dark:bg-gray-800 rounded-lg"
        >
          <div class="flex flex-col">
            <div class="w-full">
              <vue3-tailwind-datepicker
                ref="s"
                overlay
                :use-range="true"
                :formatter="formatter"
                v-model="dateValue"
                v-slot:default="{ value }"
                trigger="away"
                :disable-in-range="false"
                :start-from="new Date(2018, 0, 1)"
                :auto-apply="false"
                :disable-date="d"
                placeholder="Check"
              >
              </vue3-tailwind-datepicker>
            </div>
            <div class="flex px-2 space-x-2 mt-4">
              <button
                id="away"
                class="focus:outline-none text-sm w-24 py-2.5 rounded-md font-semibold text-white bg-blue-500 ring-0"
              >
                Show
              </button>
              <button
                class="focus:outline-none text-sm w-24 py-2.5 rounded-md font-semibold text-white bg-blue-500 ring-0"
                @click="$refs.s.clearPicker()"
              >
                Show
              </button>
            </div>
            <div>
              <!--            <div class="w-1/2">-->
              <!--              <label class="block text-gray-700">-->
              <!--                <span class="text-sm xl:text-xs uppercase">-->
              <!--                  Date-->
              <!--                </span>-->
              <!--                <input-->
              <!--                    type="text"-->
              <!--                    class="block w-full px-3 py-2.5 rounded-lg text-sm placeholder-gray-300 transition-colors border border-gray-200 focus:border-indigo-300 focus:ring focus:ring-indigo-500 focus:ring-opacity-10 focus:outline-none"-->
              <!--                    placeholder="Date"-->
              <!--                    :value="value"-->
              <!--                    @input="forceUpdate"-->
              <!--                    @focusin="show()"-->
              <!--                    @focusout="hide()"-->
              <!--                />-->
              <!--              </label>-->
              <!--            </div>-->
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref, onMounted } from 'vue';
import Vue3TailwindDatepicker from '@/litepie-datepicker.vue';
import 'tailwindcss/tailwind.css';

export default defineComponent({
  name: 'ServeDev',
  components: {
    Vue3TailwindDatepicker
  },
  setup() {
    const away = ref(null);
    const dateValue = ref(null);
    const shortcuts = () => {
      return [
        {
          label: 'Tomorrow',
          atClick: () => {
            const date = new Date();
            return [new Date(date.setDate(date.getDate() + 1)), date];
          }
        },
        {
          label: 'Last Years',
          atClick: () => {
            const date = new Date();
            return [
              new Date(date.setFullYear(date.getFullYear() - 1)),
              new Date()
            ];
          }
        }
      ];
    };
    onMounted(() => {
      // dateValue.value = {
      //   startDate: new Date(2021, 9, 1),
      //   endDate: '2021-09-01'
      // };
      dateValue.value = [new Date(2019, 9, 8), new Date(2019, 9, 19)];
      // dateValue.value = `${new Date(2019, 9, 8).toString()} ~ ${new Date(
      //   2019,
      //   9,
      //   8
      // ).toString()}`;
    });
    const d = date => {
      const today = new Date();
      return date > new Date(2021, 4, 5);
    };
    return {
      dateValue,
      d,
      shortcuts,
      away,
      formatter: ref({
        date: 'DD MMM YYYY',
        month: 'MMM'
      })
    };
  }
});
</script>
