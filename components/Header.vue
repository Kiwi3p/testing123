<!-- Please remove this file from your project -->
<template>
  <!-- This example requires Tailwind CSS v3.0+ -->
  <div>
    <div class="px-6 pt-6 lg:px-8">
      <div>
        <nav class="flex h-9 items-center justify-between" aria-label="Global">
          <div
            class="hidden lg:block flex lg:min-w-0 lg:flex-1"
            aria-label="Global"
          >
            <a href="/" class="-m-1.5 p-1.5">
              <span class="sr-only">Your Company</span>
              <img
                class="h-8"
                src="https://uploads-ssl.webflow.com/631b8bcafde15c05a06e9106/636c1a2c1b886a4ca4f3f2c6_lawtrades_logo_with_type_black.svg"
                alt=""
              />
            </a>
          </div>

          <div class="hidden lg:flex lg:min-w-0 lg:flex-1 lg:justify-end">
            <a
              href="/positions"
              class="inline-block rounded-lg px-3 py-1.5 text-sm font-semibold leading-6 text-gray-900 shadow-sm ring-1 ring-gray-900/10 hover:ring-gray-900/20"
              >Open Positions</a
            >
          </div>
        </nav>
        <!-- Mobile menu, show/hide based on menu open state. -->
        <div role="dialog" aria-modal="true">
          <div
            focus="true"
            class="bg-white fixed h-20 inset-0 z-10 overflow-y-auto px-6 py-6 lg:hidden"
          >
            <div class="flex h-9 items-center justify-between">
              <div class="flex">
                <a href="/" class="-m-1.5 p-1.5">
                  <span class="sr-only">Your Company</span>
                  <img
                    class="h-8"
                    src="https://uploads-ssl.webflow.com/631b8bcafde15c05a06e9106/636c1a2c1b886a4ca4f3f2c6_lawtrades_logo_with_type_black.svg"
                    alt=""
                  />
                </a>
              </div>
              <div class="flex">
                <a
                  href="#"
                  class="-mx-3 block rounded-lg py-2.5 px-3 text-sm font-semibold leading-6 text-gray-900 hover:bg-gray-400/10"
                  >Positions</a
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script></script>
