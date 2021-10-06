<template>
  <div class="clear-both py-6 bg-white">
    <div class="block">
      <nav
        class="
          relative
          z-0
          flex
          divide-x divide-gray-200
          rounded-full
          border
          mx-2
          overflow-hidden
          bg-white
        "
        aria-label="Tabs"
      >
        <span
          v-for="(tab, tabIdx) in tabs"
          :key="tabIdx"
          :href="tab.href"
          @click="(_e) => activeTab(tabIdx)"
          :class="[
            !!tab.current
              ? 'text-white bg-green-mint'
              : 'text-green-900 hover:text-gray-700',
            tabIdx === 0 ? 'rounded-l-lg bg-green-mint' : '',
            tabIdx === tabs.length - 1 ? 'rounded-r-lg' : '',
            'group relative min-w-0 flex-1 overflow-hidden bg-white p-2 text-sm font-medium text-center hover:bg-gray-50 focus:z-10',
          ]"
          :aria-current="tab.current ? 'tab' : undefined"
        >
          <span>{{ tab.name }}</span>
        </span>
      </nav>
      <div>
        <section
          v-for="(tab) in tabs"
          :key="tab.key"
          :class="[tab.current ? '' : 'hidden']"
        >
          <About v-bind:title="tab.title" />
        </section>
      </div>
    </div>
  </div>
</template>

 <script>
const tabs = [
  {
    name: 'Arbeitnehmer',
    key: 'arbeitnehmer',

    href: '#',
    current: true,
    title: 'Drei einfache Schritte zu deinem neuen Job',
  },
  {
    name: 'Arbeitgeber',
    key: 'arbeitgeber',

    href: '#',
    current: false,
    title: 'Drei einfache Schritte zu deinem neuen Mitarbeiter',
  },
  {
    name: 'Temporärbüro',
    key: 'temporärbüro',
    href: '#',
    current: false,
    title: 'Drei einfache Schritte zur Vermittlung neuer Mitarbeiter',
  },
]

export default {
  data: () => ({
      tabs,
  }),

  methods: {
    activeTab(tabIdx) {
      this.tabs.forEach((t,idx) => {
        if (idx === tabIdx) t.current = true;
        else t.current = false;
        return t;
      });
      return false;
      // this.tabs = tabs.forEach((t,idx) => {
      //   if (idx === tabIdx) t.current = true;
      //   else t.current = false;
      //   return t;
      // })
      // this.$set(
      //   this.tabs,
      //   [
      //     { name: 'Arbeitnehmer', href: '#', current: false },
      //     { name: 'Arbeitgeber', href: '#', current: true },
      //     { name: 'Temporärbüro', href: '#', current: false },
      //   ],
      //   true
      // )
    },
  },
}
</script>
