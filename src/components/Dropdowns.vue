<template>
  <Menu as="div" class="relative inline-block text-left">
    <div>
      <MenuButton
        class="inline-flex w-full justify-center gap-x-1 px-2 py-2 text-base
        font-semibold text-gray-800 hover:text-gray-500"
      >
        <slot></slot>
        <ChevronDownIcon class="-mr-1 h-5 w-5 text-gray-400" aria-hidden="true" />
      </MenuButton>
    </div>
    <transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transform opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-from-class="transform opacity-100 scale-100"
      leave-to-class="transform opacity-0 scale-95"
    >
      <MenuItems
        class="absolute right-0 z-10 mt-2 w-56 origin-top-right divide-y
         divide-gray-100 rounded-md bg-white shadow-lg ring-1 ring-black
         ring-opacity-5 focus:outline-none font-normal text-center"
      >
        <div class="py-1 divide-y divide-gray-100">
          <MenuItem v-slot="{ active }">
            <a
              href="#"
              :class="[
                active ? 'bg-gray-100 text-gray-900 ' : 'text-gray-700',
                'block px-4 py-2 text-sm'
              ]"
            >
              <Menu as="div" class="relative inline-block text-left">
                <div>
                  <MenuButton
                    class="inline-flex w-full justify-center gap-x-1 border-none
                     px-2 py-2 text-sm font-semibold text-gray-800 hover:text-gray-500"
                  >
                    <ChevronLeftIcon class="-ml-9 h-5 w-5 text-gray-400" aria-hidden="true" />
                    Mis cuentas
                  </MenuButton>
                </div>
                <MenuItems
                  class="absolute right-40 z-10 mt-29 w-56 origin-top-right divide-y
                   divide-gray-100 rounded-md bg-white shadow-lg focus:outline-none
                   font-normal ext-center"
                >
                  <div class="py-1 divide-y divide-gray-100">
                    <MenuItem v-slot="{ active }">
                      <a
                        href="#"
                        :class="[
                          active ? 'bg-green-100 text-gray-900 ' : 'text-gray-700',
                          'block px-4 py-2 text-sm'
                        ]"
                        ><button class="rounded-full bg-gray-300 w-7 h-7 ring-1 ring-gray-400">
                          S1
                        </button>
                        <strong> Sesame 1 </strong>
                        <slot></slot>
                        <div class="px-8 text-gray-400 text-xs">Hoy llevas 00:00</div>
                      </a>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <a
                        href="#"
                        :class="[
                          active ? 'bg-green-100 text-gray-900' : 'text-gray-700',
                          'block px-4 py-2 text-sm rounded-lg'
                        ]"
                        ><button class="rounded-full bg-gray-300 w-7 h-7 ring-1 ring-gray-400">
                          S2
                        </button>
                        <strong> Sesame 2 </strong>
                        <slot></slot>
                        <div class="px-8 text-gray-400 text-xs">Hoy llevas 00:00</div></a
                      >
                    </MenuItem>
                  </div>
                </MenuItems>
              </Menu>
            </a>
          </MenuItem>
          <MenuItem v-slot="{ active }">
            <a
              href="#"
              :class="[
                active ? 'bg-gray-100 text-gray-900' : 'text-gray-700',
                'block px-4 py-2 text-sm'
              ]"
              >Vista empleado</a
            >
          </MenuItem>
        </div>
        <div class="py-1 divide-y divide-gray-100">
          <MenuItem v-slot="{ active }">
            <a
              href="#"
              :class="[
                active ? 'bg-green-100 text-gray-900' : 'text-gray-700',
                'block px-4 py-2 text-sm'
              ]"
              >Mi perfil</a
            >
          </MenuItem>
          <MenuItem v-slot="{ active }">
            <a
              href="#"
              :class="[
                active ? 'bg-green-100 text-gray-900' : 'text-gray-700',
                'block px-4 py-2 text-sm'
              ]"
              >Cerrar sesión</a
            >
          </MenuItem>
        </div>
      </MenuItems>
    </transition>
  </Menu>
</template>
<script setup>
import {
  Menu, MenuButton, MenuItem, MenuItems,
} from '@headlessui/vue';
import { ChevronDownIcon, ChevronLeftIcon } from '@heroicons/vue/20/solid';
</script>
