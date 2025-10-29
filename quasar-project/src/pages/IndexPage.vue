<template>
  <q-page class="hacker-page">
    <div class="container q-pa-xl">
      <!-- Hero Section -->
      <div class="hero-section q-mb-xl text-center">
        <div class="avatar-container q-mb-md">
          <q-avatar size="200px" class="hacker-avatar">
            <img src="/src/assets/images/FB_IMG_1757133029745.jpg" alt="Profile" />
            <div class="avatar-overlay">
              <q-icon name="check_circle" color="green" size="40px" />
            </div>
          </q-avatar>
        </div>

        <div class="terminal-text q-mb-sm">
          <span class="text-grey-5">&gt; ./initialize_profile.sh</span>
        </div>

        <h1 class="hero-title text-green q-mb-sm">
          <span class="glitch" data-text="RONAL WALDOMORA AYBAR">
            RONAL WALDOMORA AYBAR
          </span>
        </h1>

        <div class="hero-subtitle text-white q-mb-md">
          <q-icon name="code" color="green" size="sm" class="q-mr-xs" />
          Full Stack Developer | Hacker Mindset | Problem Solver
        </div>

        <div class="tech-tags q-mt-md">
          <q-chip
            v-for="tech in techStack"
            :key="tech"
            color="dark"
            text-color="green"
            icon="terminal"
            class="tech-chip"
          >
            {{ tech }}
          </q-chip>
        </div>
      </div>

      <!-- About Section -->
      <q-card class="hacker-card q-mb-lg" dark>
        <q-card-section>
          <div class="card-header q-mb-md">
            <q-icon name="person" color="green" size="md" />
            <span class="text-h5 text-green q-ml-sm">[SOBRE_MÍ]</span>
          </div>
          <div class="text-white">
            Apasionado por la tecnología y el desarrollo web, con experiencia en la
            creación de aplicaciones modernas y responsivas. Mi enfoque es resolver
            problemas complejos con código limpio y eficiente, siempre buscando
            aprender nuevas tecnologías y metodologías.
          </div>
        </q-card-section>
      </q-card>

      <!-- Skills Grid -->
      <div class="row q-col-gutter-lg q-mb-lg">
        <div class="col-12 col-md-6">
          <q-card class="hacker-card" dark>
            <q-card-section>
              <div class="card-header q-mb-md">
                <q-icon name="code" color="green" size="md" />
                <span class="text-h6 text-green q-ml-sm">FRONTEND</span>
              </div>
              <q-list dark separator>
                <q-item v-for="skill in frontendSkills" :key="skill.name">
                  <q-item-section>
                    <q-item-label class="text-white">{{ skill.name }}</q-item-label>
                    <q-linear-progress
                      :value="skill.level / 100"
                      color="green"
                      class="q-mt-sm"
                      size="8px"
                    />
                  </q-item-section>
                </q-item>
              </q-list>
            </q-card-section>
          </q-card>
        </div>

        <div class="col-12 col-md-6">
          <q-card class="hacker-card" dark>
            <q-card-section>
              <div class="card-header q-mb-md">
                <q-icon name="storage" color="green" size="md" />
                <span class="text-h6 text-green q-ml-sm">BACKEND</span>
              </div>
              <q-list dark separator>
                <q-item v-for="skill in backendSkills" :key="skill.name">
                  <q-item-section>
                    <q-item-label class="text-white">{{ skill.name }}</q-item-label>
                    <q-linear-progress
                      :value="skill.level / 100"
                      color="green"
                      class="q-mt-sm"
                      size="8px"
                    />
                  </q-item-section>
                </q-item>
              </q-list>
            </q-card-section>
          </q-card>
        </div>
      </div>

      <!-- Experience Section -->
      <q-card class="hacker-card q-mb-lg" dark>
        <q-card-section>
          <div class="card-header q-mb-md">
            <q-icon name="work_history" color="green" size="md" />
            <span class="text-h5 text-green q-ml-sm">[EXPERIENCIA]</span>
          </div>
          <q-timeline color="green" dark>
            <q-timeline-entry
              v-for="exp in experience"
              :key="exp.title"
              :title="exp.title"
              :subtitle="exp.period"
              icon="terminal"
            >
              <div class="text-white">{{ exp.description }}</div>
            </q-timeline-entry>
          </q-timeline>
        </q-card-section>
      </q-card>

      <!-- Contact Section -->
      <q-card class="hacker-card" dark>
        <q-card-section>
          <div class="card-header q-mb-md">
            <q-icon name="contact_mail" color="green" size="md" />
            <span class="text-h5 text-green q-ml-sm">[CONTACTO]</span>
          </div>
          <div class="row q-col-gutter-md">
            <div class="col-12 col-sm-6 col-md-4">
              <q-btn
                flat
                dense
                icon="email"
                label="Email"
                color="green"
                class="full-width contact-btn"
                href="mailto:ronal.waldomora@gmail.com"
              />
            </div>
            <div class="col-12 col-sm-6 col-md-4">
              <q-btn
                flat
                dense
                icon="code"
                label="GitHub"
                color="green"
                class="full-width contact-btn"
                href="https://github.com/kcarbzz"
                target="_blank"
              />
            </div>
            <div class="col-12 col-sm-6 col-md-4">
              <q-btn
                flat
                dense
                icon="work"
                label="LinkedIn"
                color="green"
                class="full-width contact-btn"
                href="https://linkedin.com/in/ronalwaldomora"
                target="_blank"
              />
            </div>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script setup>
const techStack = ['Vue.js', 'Quasar', 'Node.js', 'JavaScript', 'TypeScript', 'Python']

const frontendSkills = [
  { name: 'Vue.js / Quasar', level: 90 },
  { name: 'HTML5 / CSS3', level: 95 },
  { name: 'JavaScript / TypeScript', level: 85 },
  { name: 'Responsive Design', level: 90 },
]

const backendSkills = [
  { name: 'Node.js / Express', level: 80 },
  { name: 'Python / Django', level: 75 },
  { name: 'REST APIs', level: 85 },
  { name: 'Databases (SQL/NoSQL)', level: 80 },
]

const experience = [
  {
    title: 'Desarrollo Web Full Stack',
    period: '2023 - Presente',
    description:
      'Desarrollo de aplicaciones SPA con Vue y Quasar, integración de APIs REST y optimización de rendimiento.',
  },
  {
    title: 'Frontend Developer',
    period: '2022 - 2023',
    description: 'Diseño e implementación de interfaces UX/UI modernas y responsivas.',
  },
  {
    title: 'Backend Developer',
    period: '2021 - 2022',
    description:
      'Desarrollo de APIs REST, gestión de bases de datos y despliegue en producción.',
  },
]
</script>

<style scoped>
.hacker-page {
  background: linear-gradient(135deg, #0a0e27 0%, #16213e 50%, #0f3460 100%);
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.hero-section {
  padding: 40px 20px;
}

.avatar-container {
  position: relative;
  display: inline-block;
}

.hacker-avatar {
  border: 3px solid #00ff41;
  box-shadow: 0 0 30px rgba(0, 255, 65, 0.5);
  position: relative;
  overflow: visible;
}

.avatar-overlay {
  position: absolute;
  bottom: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.8);
  border-radius: 50%;
  padding: 5px;
}

.terminal-text {
  font-family: 'Courier New', monospace;
  font-size: 14px;
}

.hero-title {
  font-family: 'Courier New', monospace;
  font-size: 2.5rem;
  font-weight: bold;
  text-shadow: 0 0 20px #00ff41;
  margin: 0;
}

.glitch {
  position: relative;
  display: inline-block;
  animation: glitch 3s infinite;
}

@keyframes glitch {
  0%,
  100% {
    text-shadow: 0 0 20px #00ff41;
  }
  25% {
    text-shadow:
      -2px 0 0 #ff00ff,
      2px 0 0 #00ffff;
  }
  50% {
    text-shadow: 0 0 20px #00ff41;
  }
  75% {
    text-shadow:
      2px 0 0 #ff00ff,
      -2px 0 0 #00ffff;
  }
}

.hero-subtitle {
  font-size: 1.2rem;
  opacity: 0.9;
}

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
}

.tech-chip {
  border: 1px solid #00ff41;
  transition: all 0.3s ease;
}

.tech-chip:hover {
  transform: scale(1.05);
  box-shadow: 0 0 15px rgba(0, 255, 65, 0.5);
}

.hacker-card {
  background: rgba(15, 15, 35, 0.8);
  border: 1px solid #00ff41;
  border-radius: 12px;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.hacker-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 255, 65, 0.3);
}

.card-header {
  display: flex;
  align-items: center;
  font-family: 'Courier New', monospace;
}

.contact-btn {
  border: 1px solid #00ff41;
  transition: all 0.3s ease;
}

.contact-btn:hover {
  background: rgba(0, 255, 65, 0.1);
  box-shadow: 0 0 15px rgba(0, 255, 65, 0.5);
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 1.8rem;
  }

  .hero-subtitle {
    font-size: 1rem;
  }
}
</style>
