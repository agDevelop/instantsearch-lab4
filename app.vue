<template>
  <div>
    <NuxtLayout>
      <div
        class="w-[800px] flex justify-center items-center text-start text-xl ml-6 h-12"
      >
        <b>Гончаров А.Н. 224-372</b>
      </div>
      <div class="flex flex-col gap-2 justify-center items-center mt-8">
        <div class="w-[700px] flex flex-col">
          <div class="text-stone-600 relative mb-3">
            <div
              :class="[
                focus ? 'text-emerald-300' : 'text-gray-300',
                'w-4 h-4 my-auto z-10 absolute top-0 bottom-0 left-3',
              ]"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 16 16"
                fill="currentColor"
                class="w-4 h-4"
              >
                <path
                  fill-rule="evenodd"
                  d="M9.965 11.026a5 5 0 1 1 1.06-1.06l2.755 2.754a.75.75 0 1 1-1.06 1.06l-2.755-2.754ZM10.5 7a3.5 3.5 0 1 1-7 0 3.5 3.5 0 0 1 7 0Z"
                  clip-rule="evenodd"
                />
              </svg>
            </div>
            <input
              class="w-full py-2 pl-9 pr-1 rounded-md border-2 shadow-inner focus:outline-none focus:border-emerald-300"
              type="text"
              v-model="input"
              @focus="focus = true"
              @blur="focus = false"
            />
          </div>

          <p
            class="text-stone-800 border-stone-300 -mt-px py-3 px-4 text-sm font-medium last:border-none focus:z-10 border-b-2 disabled:opacity-disabled:pointer-events-none"
            v-for="thing in filterThings()"
            :key="thing.id"
            :value="thing"
          >
            {{ thing.content }}
          </p>
        </div>
      </div>
    </NuxtLayout>
  </div>
</template>

<script setup>
import { ref } from "vue";

const thingsList = [
  {
    id: 0,
    content: "Веб разработка",
  },
  {
    id: 1,
    content: "Веб дизайн",
  },
  {
    id: 2,
    content: "Нейросети",
  },
  {
    id: 3,
    content: "Мобильная разработка",
  },
];

var input = ref("");
var focus = ref(false);

function filterThings() {
  return thingsList.filter((e) =>
    e.content.toLowerCase().includes(input.value.toLowerCase())
  );
}
</script>
