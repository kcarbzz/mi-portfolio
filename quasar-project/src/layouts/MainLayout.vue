<template>
  <q-layout view="lHh Lpr lFf" class="hacker-theme">
    <q-header elevated class="bg-dark glossy">
      <q-toolbar class="toolbar-hacker">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
          class="glow-btn"
        />

        <q-toolbar-title class="terminal-title">
          <span class="text-green">&gt;</span>
          <span class="typing-text">Ronal_Waldomora.dev</span>
        </q-toolbar-title>

        <div class="text-grey-4 text-caption">[ System Online ]</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-dark text-green drawer-hacker"
    >
      <q-scroll-area class="fit">
        <div class="q-pa-md">
          <div class="text-h6 text-green q-mb-md terminal-header">
            <q-icon name="terminal" class="q-mr-sm" />
            MENU.EXE
          </div>

          <q-separator dark class="q-mb-md" />

          <q-list dark>
            <q-item
              v-for="section in menuSections"
              :key="section.name"
              clickable
              v-ripple
              :to="section.route"
              class="menu-item-hacker"
            >
              <q-item-section avatar>
                <q-icon :name="section.icon" color="green" />
              </q-item-section>

              <q-item-section>
                <q-item-label class="text-white">{{ section.name }}</q-item-label>
                <q-item-label caption class="text-grey-5">
                  {{ section.caption }}
                </q-item-label>
              </q-item-section>
            </q-item>
          </q-list>

          <q-separator dark class="q-my-md" />

          <div class="text-caption text-grey-5 q-pa-sm terminal-footer">
            <div>> STATUS: CONNECTED</div>
            <div>> UPTIME: {{ uptime }}</div>
          </div>
        </div>
      </q-scroll-area>
    </q-drawer>

    <q-page-container class="page-container-hacker">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const menuSections = [
  {
    name: 'Inicio',
    caption: 'Página principal',
    icon: 'home',
    route: '/',
  },
  {
    name: 'Sobre Mí',
    caption: 'Conoce mi historia',
    icon: 'person',
    route: '/about',
  },
  {
    name: 'Habilidades',
    caption: 'Stack tecnológico',
    icon: 'code',
    route: '/skills',
  },
  {
    name: 'Proyectos',
    caption: 'Mi portafolio',
    icon: 'work',
    route: '/projects',
  },
  {
    name: 'Experiencia',
    caption: 'Trayectoria profesional',
    icon: 'business_center',
    route: '/experience',
  },
  {
    name: 'Contacto',
    caption: 'Conecta conmigo',
    icon: 'email',
    route: '/contact',
  },
]

const leftDrawerOpen = ref(false)
const uptime = ref('00:00:00')

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}

onMounted(() => {
  const startTime = Date.now()
  setInterval(() => {
    const elapsed = Math.floor((Date.now() - startTime) / 1000)
    const hours = Math.floor(elapsed / 3600)
      .toString()
      .padStart(2, '0')
    const minutes = Math.floor((elapsed % 3600) / 60)
      .toString()
      .padStart(2, '0')
    const seconds = (elapsed % 60).toString().padStart(2, '0')
    uptime.value = `${hours}:${minutes}:${seconds}`
  }, 1000)
})
</script>

<style scoped>
.hacker-theme {
  background: linear-gradient(135deg, #0a0e27 0%, #1a1a2e 100%);
}

.toolbar-hacker {
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid #00ff41;
}

.terminal-title {
  font-family: 'Courier New', monospace;
  font-weight: bold;
  letter-spacing: 2px;
}

.text-green {
  color: #00ff41;
  text-shadow: 0 0 10px #00ff41;
}

.typing-text {
  color: #00ff41;
  animation: typing 2s steps(40) 1s infinite alternate;
}

@keyframes typing {
  from {
    opacity: 1;
  }
  to {
    opacity: 0.7;
  }
}

.glow-btn {
  transition: all 0.3s ease;
}

.glow-btn:hover {
  box-shadow: 0 0 15px #00ff41;
}

.drawer-hacker {
  background: linear-gradient(180deg, #0f0f23 0%, #1a1a2e 100%);
  border-right: 1px solid #00ff41;
}

.terminal-header {
  font-family: 'Courier New', monospace;
  text-shadow: 0 0 10px #00ff41;
}

.menu-item-hacker {
  border-radius: 8px;
  margin-bottom: 8px;
  transition: all 0.3s ease;
}

.menu-item-hacker:hover {
  background: rgba(0, 255, 65, 0.1);
  border-left: 3px solid #00ff41;
  transform: translateX(5px);
}

.terminal-footer {
  font-family: 'Courier New', monospace;
  border-top: 1px solid #00ff41;
  background: rgba(0, 0, 0, 0.3);
  border-radius: 4px;
}

.page-container-hacker {
  background: linear-gradient(135deg, #0a0e27 0%, #16213e 50%, #0f3460 100%);
  min-height: 100vh;
}
</style>
