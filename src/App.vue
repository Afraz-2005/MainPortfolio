<template>
  <div id="app">
    <div 
  class="custom-cursor" 
  :style="{ transform: `translate3d(${mouseX}px, ${mouseY}px, 0)` }"
>
  <svg class="cursor-svg" width="40" height="40">
    <circle class="cursor-bg" cx="20" cy="20" r="18" />
    <circle 
      class="cursor-progress" 
      cx="20" cy="20" r="18" 
      :style="{ strokeDashoffset: strokeOffset }"
    />
  </svg>
</div>
    <header>
      <nav class="nav-container">
        <div class="nav-logo">AFRAZ.</div>
        <div class="nav-links">
          <a href="#hero">Home</a>
          <a href="#about">About</a>
          <a href="#projects">Project</a>
        </div>
        <a href="#contact" class="nav-button">START A PROJECT →</a>
      </nav>
    </header>

    <main>
      <section id="hero" class="section-hero fade-zoom" :style="sectionParallaxStyle">
        <div class="hero-top">
          <div class="hero-copy">
            <p class="hero-subtitle">I’m Specialized in</p>
            <h1>Creating Apps & Designs.</h1>
          </div>
          <div class="hero-image" :style="[{ backgroundImage: `url(${heroImage})` }, heroImageStyle]"></div>
        </div>
        <h2 class="hero-brand" :style="heroBrandStyle">AFRAZ</h2>
      </section>

      <section id="projects" class="section projects-section fade-zoom" :style="sectionParallaxStyle">
        <div class="section-header">
          <div class="section-label">Featured Work</div>
          <div class="section-title">Recent projects designed to stand out.</div>
        </div>
        <div class="project-grid">
          <div 
            v-for="(project, index) in visibleProjects"
            :key="project.id"
            :class="['project-card', project.size, project.imageClass, 'fade-zoom']"
            :style="projectCardStyle"
          >
            <a :href="project.url" class="project-link" target="_blank" style="cursor: crosshair;"><span>View Project</span></a>
          </div>
        </div>
        <div class="projects-footer">
          <!-- <button class="ghost-button" @click="toggleProjects">
            {{ showAllProjects ? 'Show Less' : 'Load More' }}
          </button> -->
        </div>
      </section>

      <section class="section services-section fade-zoom" :style="sectionParallaxStyle">
        <div class="section-heading-row">
          <h2>My Services</h2>
        </div>
        <div class="services-list" style="cursor: crosshair;">
          <div v-for="service in services" :key="service.id" class="service-block fade-zoom" :style="serviceBlockStyle">
            <button style="cursor: crosshair;" class="service-row" @click="toggleService(service) ">
              <span class="service-index">{{ service.id }}</span>
              <span class="service-text">{{ service.title }}</span>
              <span class="service-action">{{ service.open ? '–' : '+' }}</span>
            </button>
            <transition name="slide-fade">
              <p v-if="service.open" class="service-description">{{ service.description }}</p>
            </transition>
          </div>
        </div>
      </section>

      <section id="about" class="section about-section fade-zoom" :style="sectionParallaxStyle">
        <div class="about-grid">
          <div class="about-copy">
            <h2>About Me</h2>
            <p>
              I’m a programmer focused on <strong>Web, Digital design</strong> and modern
              branding — creating polished experiences that feel both premium and effortless.
            </p>
            <p>
              With a strong eye for detail and a user-first mindset, I create websites, apps and digital
              products that not only look great but also work seamlessly. I play guitar and sing when I’m not busy.
            </p>
            <div class="about-actions">
              <a href="#" style="cursor: crosshair;" class="ghost-button">View Resume →</a>
              <div class="social-links" style="cursor: crosshair;">
                <a style="cursor: crosshair;" href="https://github.com/Afraz-2005">GT</a>
                <a style="cursor: crosshair;" href="https://www.instagram.com/afr.z.x_/" target="_">IG</a>
                <a style="cursor: crosshair;" href="https://x.com/__Afraz05__">X</a>
              </div>
            </div>
          </div>
          <div class="about-image fade-zoom" :style="aboutImageStyle"></div>
        </div>
      </section>

      <section class="section testimonials-section fade-zoom" :style="sectionParallaxStyle">
        <div class="section-top-row">
          <h2>Testimonials</h2>
          <div style="cursor: crosshair;" class="slider-controls">
            <button aria-label="Previous">‹</button>
            <button aria-label="Next">›</button>
          </div>
        </div>
        <div class="testimonial-grid">
          <div v-for="testimonial in testimonials" :key="testimonial.name" class="testimonial-card fade-zoom" :style="testimonialStyle">
            <p>“{{ testimonial.quote }}”</p>
            <div class="testimonial-meta">
              <a :href="testimonial.url" target="_blank" class="testimonial-link" style="cursor: crosshair;">
                <div class="testimonial-avatar" :style="{ backgroundImage: `url(${testimonial.image})` }"></div>
                <div>
                  <strong>{{ testimonial.name }}</strong>
                  <span>{{ testimonial.role }}</span>
                </div>
              </a>
            </div>
          </div>
        </div>
      </section>

      <section class="section faq-section fade-zoom" :style="sectionParallaxStyle">
        <div class="faq-grid">
          <div class="faq-title-block">
            <h2>Common Questions</h2>
            <p>Answers to the questions I get asked most often.</p>
          </div>
          <div class="faq-list">
            <div v-for="item in faqs" :key="item.question" class="faq-item fade-zoom" :style="faqItemStyle">
              <button style="cursor: crosshair;" class="faq-question" @click="toggleFaq(item)">
                <span>{{ item.question }}</span>
                <span class="faq-sign">+</span>
              </button>
              <transition name="slide-fade">
                <p v-if="item.open" class="faq-answer">{{ item.answer }}</p>
              </transition>
            </div>
          </div>
        </div>
      </section>

      <section id="contact" class="section contact-section fade-zoom" :style="sectionParallaxStyle">
        <div class="contact-card">
          <div>
            <h2>Email me → </h2>
            <a href="https://mail.google.com/mail/?view=cm&fs=1&to=imamafraz.sp2210@gmail.com" target="_blank" style="cursor: crosshair;" >click here: imamafraz.sp2210@gmail.com</a>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <span>© 2026 Afraz Imam Mahbir, All Rights Reserved</span>
    </footer>
  </div>
</template>

<script>
import { reactive, ref, computed, onMounted, onUnmounted } from 'vue'
import heroImage from '../heroImage.jpg'
import DK from '../DK.png'
// import avatar2 from '../assets/avatar2.jpg'
// import avatar3 from '../assets/avatar3.jpg'

export default {
  setup() {
    const mouseX = ref(0)
    const mouseY = ref(0)
    const scrollProgress = ref(0)
    const circumference = 2 * Math.PI * 18

const strokeOffset = computed(() => {
  return circumference - (scrollProgress.value / 100) * circumference
})

function updateCursor(e) {
  mouseX.value = e.clientX
  mouseY.value = e.clientY
}

function updateScrollProgress() {
  const h = document.documentElement
  const b = document.body
  const st = 'scrollTop'
  const sh = 'scrollHeight'
  
  // Calculate percentage: (current scroll / total scrollable height) * 100
  const percent = (h[st] || b[st]) / ((h[sh] || b[sh]) - h.clientHeight) * 100
  scrollProgress.value = percent
}

onMounted(() => {
  window.addEventListener('mousemove', updateCursor)
  window.addEventListener('scroll', updateScrollProgress)
})

onUnmounted(() => {
  window.removeEventListener('mousemove', updateCursor)
  window.removeEventListener('scroll', updateScrollProgress)
})

    const services = reactive([
      {
        id: '01',
        title: 'Website/Webapp',
        description: 'Designing and creating premium website/webapp experiences with clean visuals, clear hierarchy, and strong visual detailing.',
        open: false
      },
      {
        id: '02',
        title: 'UI/UX Design',
        description: 'Crafting intuitive interfaces with human-centered interactions and polished motion design.',
        open: false
      },
      {
        id: '03',
        title: 'Logo & Branding',
        description: 'Developing brand identities that feel consistent, memorable, and elevated across digital touchpoints.',
        open: false
      },
      {
        id: '04',
        title: 'Graphics',
        description: 'Creating stunning visual content for digital and print media.',
        open: false
      }
    ])

    const projectItems = reactive([
      { id: 'p1', size: 'project-card-large', imageClass: 'project-image-1', url: 'https:/google.com' },
      { id: 'p2', size: 'project-card-large', imageClass: 'project-image-2', url: 'https://covid-cross.netlify.app' },
      { id: 'p3', size: 'project-card-small', imageClass: 'project-image-3', url: 'https://hedan.netlify.app' },
      { id: 'p4', size: 'project-card-small', imageClass: 'project-image-4', url: 'https://afraz-2005.github.io/GR/' },
      // { id: 'a', size: 'project-link', Text: 'View Project', url: 'https://afraz-2005.github.io/GR/' }
    ])


    const showAllProjects = ref(false)
    const scrollY = ref(0)

    function handleScroll() {
      scrollY.value = window.scrollY
    }

    const heroImageStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.15, 150) - 18}px`
    }))

    const heroBrandStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.12, 100)}px`
    }))

    const sectionParallaxStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.012, 60)}px`
    }))

    const projectCardStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.04, 70)}px`
    }))

    const aboutImageStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.05, 60)}px`
    }))

    const serviceBlockStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.03, 60)}px`
    }))

    const testimonialStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.02, 60)}px`
    }))

    const faqItemStyle = computed(() => ({
      '--parallax': `${Math.min(scrollY.value * 0.025, 60)}px`
    }))

    let fadeObserver = null

    onMounted(() => {
      handleScroll()
      window.addEventListener('scroll', handleScroll, { passive: true })

      fadeObserver = new IntersectionObserver(
        (entries) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add('in-view')
            } else {
              entry.target.classList.remove('in-view')
            }
          })
        },
        { threshold: 0.20, rootMargin: '0px 0px -100px 0px' }
      )

      document.querySelectorAll('.fade-zoom').forEach((el) => fadeObserver.observe(el))
    })

    onUnmounted(() => {
      window.removeEventListener('scroll', handleScroll)
      if (fadeObserver) {
        fadeObserver.disconnect()
      }
    })

    const testimonials = [
      {
        name: 'Tawkir Taki Tajwar',
        role: 'CEO-Dhakaiya Kitchen',
        quote:'Afraz delivers splendid, premium designs that truly resonate. Every detail feels intentional and meaningful, elevated by smooth interactions. A top-tier experience that perfectly balances modern aesthetic with clear, high-impact functional purpose.',
        image: DK,
        url: 'https://www.facebook.com/people/Dhakaiya-Kitchen-Catering-Services/61576047194774/'
      },
      {
        name: 'Emily',
        role: 'Marketing Head',
        quote:
          'I’m genuinely impressed with the final result of the portfolio website. It’s visually appealing, easy to navigate, and does an amazing job presenting my projects. The attention to detail and smooth interactions really set it apart. I’ve already seen a boost in engagement.'
      },
      {
        name: 'William',
        role: 'Founder',
        quote:
          'I’m genuinely impressed with the final result of the portfolio website. It’s visually appealing, easy to navigate, and does an amazing job presenting my projects. The attention to detail and smooth interactions really set it apart. I’ve already seen a boost in engagement.'
      }
    ]

    const faqs = reactive([
      { question: 'What service do you offer?', answer: 'I mainly create digital products, websites, sometimes apps and brand experiences with a premium visual edge.', open: false },
      { question: 'Do you use code in your projects?', answer: 'I design and build using JavaScript frameworks primarily and flutter framework to deliver polished applications, graphics are done using canva, adobe creative cloud', open: false },
      { question: 'Can you help redesign my existing website?', answer: 'Yes — I can refresh your website, improve usability, and create a more engaging online presence.', open: false },
      { question: 'How long does a typical project take?', answer: 'Most projects are completed within 1-2 weeks or 3–6 weeks depending on scope and complexity.', open: false },
      { question: 'Will I be able to edit the website after it’s done?', answer: 'Absolutely. I deliver solutions that are easy to maintain and update.', open: false }
    ])

    function toggleProjects() {
      showAllProjects.value = !showAllProjects.value
    }

    function toggleService(service) {
      service.open = !service.open
    }

    function toggleFaq(item) {
      item.open = !item.open
    }

    const visibleProjects = computed(() => {
      return showAllProjects.value ? projectItems : projectItems.slice(0, 4)
    })

    return {
      services,
      testimonials,
      faqs,
      showAllProjects,
      visibleProjects,
      toggleProjects,
      toggleService,
      toggleFaq,
      heroImage,
      heroImageStyle,
      heroBrandStyle,
      sectionParallaxStyle,
      projectCardStyle,
      aboutImageStyle,
      serviceBlockStyle,
      testimonialStyle,
      faqItemStyle,
      mouseX,
      mouseY,
      strokeOffset
    }
  }
}
</script>

<style>
:root {
  color-scheme: dark;
  font-family: 'Switzer', sans-serif;
  background: #010101;
  color: #fff;
}

* {
  box-sizing: border-box;
}

html, body {
  cursor: none;
}

/* Ensure links and buttons still show they are clickable (optional) */
a, button {
  cursor: none;
}

.custom-cursor {
  position: fixed;
  top: -20px; /* Half of width/height to center it on the tip */
  left: -20px;
  width: 40px;
  height: 40px;
  pointer-events: none; /* Let clicks pass through */
  z-index: 9999;
  transition: transform 0.1s ease-out; /* Adds a tiny bit of "lag" for smoothness */
}

.cursor-svg {
  transform: rotate(-90deg); /* Start the progress from the top */
}

.cursor-bg {
  fill: none;
  stroke: rgba(255, 255, 255, 0.493);
  stroke-width: 2;
}

.cursor-progress {
  fill: none;
  stroke: #fff; /* Progress color */
  stroke-width: 4;
  stroke-linecap: round;
  stroke-dasharray: 113; /* Should match the circumference calculation */
  transition: stroke-dashoffset 0.1s linear;
}

html,
body,
#app {
  min-height: 100%;
  scroll-behavior: smooth;
}

body {
  margin: 0;
  background: #010101;
  color: #fff;
}

a {
  color: inherit;
  text-decoration: none;
  transition: color 0.25s ease, opacity 0.25s ease, transform 0.25s ease;
}

button {
  font: inherit;
  cursor: pointer;
  transition: background-color 0.25s ease, color 0.25s ease, border-color 0.25s ease, transform 0.25s ease, opacity 0.25s ease;
}

#app {
  overflow-x: hidden;
  position: relative;
}

header {
  position: fixed;
  inset: 0 0 auto;
  z-index: 20;
  background: rgba(1, 1, 1, 0.88);
  backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.nav-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px; /* Standard desktop height */
  transition: all 0.3s ease;
}

.nav-logo {
  letter-spacing: 0.15em;
  font-weight: 900;
  font-size: 1.1rem;
}

.nav-links {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 34px;
}

.nav-links a {
  color: #fff;
  opacity: 0.9;
  transition: opacity 0.2s ease;
}

.nav-links a:hover {
  opacity: 1;
}

.nav-button {
  border: 1px solid rgba(255, 255, 255, 0.7);
  padding: 12px 24px;
  border-radius: 999px;
  font-weight: 700;
  background: rgba(255, 255, 255, 0.05);
}

.nav-button:hover {
  background: rgba(255, 255, 255, 0.12);
  border-color: rgba(255, 255, 255, 0.95);
  transform: translateY(-1px);
}
/* MOBILE VIEW (Screens 768px and smaller) */
@media (max-width: 768px) {
  header {
    background: rgba(0, 0, 0, 0.8); /* Ensures text is visible over background images */
    backdrop-filter: blur(10px);
    width: 100%;
    position: fixed;
    top: 0;
    z-index: 1000;
  }

  .nav-container {
    padding: 10px 15px; /* This makes the navbar "very thin" */
  }

  /* 1. Hide the middle links */
  .nav-links {
    display: none;
  }

  /* 2. Style the Logo */
  .nav-logo {
    font-size: 1.1rem;
    font-weight: 800;
    letter-spacing: -0.5px;
  }

  /* 3. Style the "Start a Project" button */
  .nav-button {
    font-size: 0.75rem; /* Smaller font for mobile */
    padding: 6px 12px;
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 4px;
    text-decoration: none;
    color: #fff;
  }
}

main {
  padding-top: 84px;
}

.section {
  max-width: 1400px;
  margin: 0 auto;
  padding: 80px 40px;
}

.section-hero {
  padding-top: 90px;
  padding-bottom: 70px;
  min-height: calc(100vh - 90px);
}

.hero-top {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 60px;
  align-items: start;
  padding-right: 40px;
  position: relative;
  overflow: visible;
}

.hero-top::before {
  content: "";
  position: absolute;
  top: -38px;
  right: -68px;
  width: 680px;
  height: 520px;
  z-index: 0;
  opacity: 0.82;
  pointer-events: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' preserveAspectRatio='none' viewBox='0 0 900 700'%3E%3Cpath d='M0 140 C180 80 260 180 420 130 S700 50 900 100' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M0 200 C220 150 320 250 500 200 S700 160 900 210' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M0 260 C240 200 360 300 540 250 S760 210 900 260' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M0 320 C260 260 400 360 580 310 S780 270 900 320' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M120 380 C320 320 460 420 640 360 S820 320 900 370' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M80 440 C340 380 500 470 700 420 S840 380 900 430' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M160 500 C360 440 540 520 740 470 S860 430 900 480' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3Cpath d='M220 560 C380 500 580 560 760 510 S860 470 900 520' fill='none' stroke='rgba(255,255,255,0.8)' stroke-width='0.45'/%3E%3C/svg%3E");
  background-size: 760px 600px;
  background-repeat: no-repeat;
  background-position: 56px 0;
  filter: blur(0.08px);
  animation: hero-topo 28s linear infinite;
}

.hero-copy {
  max-width: 680px;
  padding-left: 40px;
}

@keyframes hero-topo {
  0% { background-position: right top; }
  50% { background-position: 40px 24px; }
  100% { background-position: right top; }
}

.hero-image {
  position: relative;
  z-index: 1;
  width: min(320px, calc(100% - 40px));
  aspect-ratio: 1 / 1;
  align-self: start;
  justify-self: end;
  transition: transform 0.35s ease-out;
  transform: translateY(var(--parallax, 0));
  /* background: url('https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=900&q=80'); */
  background-size: cover;
  background-position: center;
  border: 8px solid rgb(255, 255, 255);
  border-radius: 160px;
}

.hero-brand {
  transition: transform 0.35s ease-out;
  transform: translateY(var(--parallax, 0));
}

.fade-zoom {
  opacity: 0;
  --scale: 0.96;
  transform: translateY(var(--parallax, 0)) scale(var(--scale));
  transition: opacity 0.55s ease, transform 0.55s ease;
}

.fade-zoom.in-view {
  opacity: 1;
  --scale: 1;
}

.hero-brand {
  margin: 0;
  font-size: clamp(5.5rem, 12vw, 11rem);
  letter-spacing: -0.11em;
  line-height: 0.9;
  font-weight: 900;
  padding-left: 40px;
}

@media (max-width: 768px) {
  .section-hero {
    padding-top: 4px; /* Leave room for your thin navbar */
    min-height: auto;
    overflow: hidden;
  }

  /* Stack the subtitle/title and the circle image */
  .hero-top {
    flex-direction: column; 
    align-items: center;
    text-align: center;
    gap: 30px;
    
  }

  .hero-copy h1 {
    font-size: 2.5rem; /* Shrink "Creating Apps & Designs" */
    line-height: 1.1;
    font-family: Switzer;
    font-weight: 400;
  }

  /* Shrink the Circle Hero Picture */
  .hero-image {
    width: 70vw !important; 
    height: 30vh !important;
    margin: 0 auto;
    border-radius: 0%;
    border: 0;
    box-shadow: 0 0 0 2px rgba(255, 255, 255, 0.477);
    margin-top: 5vh;
    margin-bottom: 3vh;
    margin-left: 14vw;
    /* margin: 9vw; */
    
  }

  /* Shrink the Big AFRAZ text */
  .hero-brand {
    font-size: 18vw !important; /* Uses viewport width so it never overflows */
    margin-top: -20px; /* Pull it up slightly to overlap beautifully */
    letter-spacing: -2px;
    margin-left: 8vw;
    margin-right: 10vw;
    font-family: Switzer;
    font-weight: 1500 !important;
    opacity: 0;
  }
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.35s ease;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
  max-height: 0;
}

.slide-fade-enter-to,
.slide-fade-leave-from {
  opacity: 1;
  transform: translateY(0);
  max-height: 300px;
}

.service-description,
.faq-answer {
  margin: 0;
  padding: 0 0 0 24px;
  color: rgba(255, 255, 255, 0.85);
  line-height: 1.75;
  overflow: hidden;
}

.hero-subtitle {
  margin: 0 0 18px;
  font-size: 0.95rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.75);
}

.hero-copy h1 {
  margin: 0;
  font-size: clamp(3.5rem, 7vw, 5.8rem);
  line-height: 0.92;
  letter-spacing: -0.06em;
}


.projects-section {
  padding-top: 100px;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  gap: 20px;
  margin-bottom: 40px;
}

.section-label {
  font-size: 0.9rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.65);
}

.section-title {
  font-size: 1.2rem;
  max-width: 720px;
}

.project-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 24px;
}

.project-card {
  min-height: 300px;
  background-size: cover;
  background-position: center;
  border: 1px solid rgba(255, 255, 255, 0.08);
  position: relative; /* Essential for the absolute link to stay inside the card */
  cursor: crosshair !important;;
  overflow: hidden;
}

.project-card-large {
  min-height: 420px;
}

.project-card-small {
  min-height: 330px;
}

.project-image-1 {
  background-image: url('../GR.png');
}

.project-image-2 {
  background-image: url('../cc.png');
}

.project-image-3 {
  background-image: url('../Hedan.png');
}

.project-image-4 {
  background-image: url('../smr.png');
}

.project-image-5 {
  background-image: url('https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=900&q=80');
}

.project-image-6 {
  background-image: url('https://images.unsplash.com/photo-1500534314209-a25ddb2bd429?auto=format&fit=crop&w=900&q=80');
}
.project-link {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-weight: 700;
  opacity: 0;
  transition: opacity 0.25s ease;
}

.project-link:hover {
  opacity: 1;
  color: #fff !important;
  background-color: #010101a4;
  backdrop-filter: blur(5px);
  
}

/* .project-card:hover {
  opacity: 0.2;
} */
.project-card:hover {
  transform: translateY(-4px);
}


.projects-footer {
  margin-top: 32px;
  display: flex;
  justify-content: center;
}


.ghost-button {
  padding: 14px 32px;
  border-radius: 999px;
  border: 1px solid rgba(255, 255, 255, 0.6);
  background: transparent;
  color: #fff;
  font-weight: 700;
}

.ghost-button:hover {
  background: rgba(255, 255, 255, 0.07);
  border-color: rgba(255, 255, 255, 0.9);
  transform: translateY(-1px);
}

.services-section {
  border-top: 1px solid rgba(255, 255, 255, 0.081);
}

.section-heading-row {
  margin-bottom: 32px;
}

.services-list {
  display: grid;
  gap: 18px;
}

.service-row {
  display: grid;
  grid-template-columns: 72px 1fr 32px;
  align-items: center;
  gap: 18px;
  padding: 20px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  border: none;
}

.service-index {
  opacity: 0.75;
  font-weight: 700;
}

.service-text {
  font-size: 1rem;
  font-weight: 600;
}

.service-action {
  text-align: right;
  font-size: 1.4rem;
}

.service-block {
  display: grid;
  gap: 8px;
}

.service-row {
  display: grid;
  grid-template-columns: 72px 1fr 32px;
  align-items: center;
  gap: 18px;
  padding: 20px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  background: transparent;
  color: #fff;
  width: 100%;
}

.service-description {
  margin: 0 0 0 72px;
  color: rgba(255, 255, 255, 0.75);
  line-height: 1.8;
}

.about-section {
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.about-grid {
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  gap: 40px;
  align-items: center;
}

.about-copy h2 {
  margin: 0 0 24px;
  font-size: clamp(3rem, 4.5vw, 4.5rem);
}

.about-copy p {
  margin: 0 0 18px;
  max-width: 680px;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.85);
}

.about-copy strong {
  color: #fff;
}

.about-actions {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 18px;
  margin-top: 20px;
}

.social-links {
  display: flex;
  gap: 16px;
}

.social-links a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 44px;
  height: 44px;
  border-radius: 12px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  background: rgba(255, 255, 255, 0.03);
}

.about-image {
  min-height: 450px;
  background: url('../me3.jpg');
  background-size: cover;
  background-position: center;
  border: none;
}

.testimonials-section {
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.section-top-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  margin-bottom: 36px;
}

.section-top-row h2 {
  margin: 0;
}

.slider-controls {
  display: flex;
  gap: 14px;
}

.slider-controls button {
  width: 52px;
  height: 52px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 14px;
  background: rgba(255, 255, 255, 0.03);
  color: #fff;
  font-size: 1.5rem;
}

.testimonial-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
}

.testimonial-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 24px;
  padding: 32px;
  min-height: 320px;
}

.testimonial-card p {
  margin: 0 0 32px;
  line-height: 1.85;
  color: rgba(255, 255, 255, 0.88);
}

.testimonial-meta {
  display: flex;
  align-items: center;
  gap: 16px;
}

.testimonial-avatar {
  width: 58px;
  height: 58px;
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.08);
}

.testimonial-meta strong {
  display: block;
  font-size: 1rem;
}

.testimonial-meta span {
  display: block;
  margin-top: 4px;
  color: rgba(255, 255, 255, 0.7);
}
.testimonial-avatar {
  width: 58px;
  height: 58px;
  border-radius: 18px; /* Your existing style */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-color: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.08);
  flex-shrink: 0; /* Prevents the avatar from squishing if text is long */
}
.testimonial-card:hover .testimonial-avatar {
  transform: scale(1.1);
  border-color: rgba(255, 255, 255, 0.5);
  transition: all 0.3s ease;
}
.testimonial-link {
  display: flex;
  align-items: center;
  gap: 16px;
  text-decoration: none;
  color: inherit; /* Keeps the text white */
  transition: opacity 0.3s ease;
}

.testimonial-link:hover {
  opacity: 0.8;
}

.testimonial-avatar {
  /* Ensure your existing avatar styles are here */
  flex-shrink: 0;
  transition: transform 0.3s ease, border-color 0.3s ease;
}

/* Added interaction: Avatar grows when you hover the name/link */
.testimonial-link:hover .testimonial-avatar {
  transform: scale(1.1);
  border-color: rgba(255, 255, 255, 0.4);
}

.faq-section {
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.faq-grid {
  display: grid;
  grid-template-columns: 0.9fr 1fr;
  gap: 40px;
  align-items: start;
}

.faq-title-block h2 {
  margin: 0 0 18px;
  font-size: clamp(3.2rem, 5vw, 4.8rem);
}

.faq-title-block p {
  margin: 0;
  color: rgba(255, 255, 255, 0.75);
  max-width: 420px;
  line-height: 1.8;
}

.faq-list {
  display: grid;
  gap: 16px;
}

.faq-item {
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.faq-question {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 22px 0;
  background: transparent;
  color: #fff;
  border: none;
}

.faq-question span:first-child {
  text-align: left;
  font-size: 1rem;
}

.faq-sign {
  font-size: 1.4rem;
  color: rgba(255, 255, 255, 0.9);
}

.faq-answer {
  margin: 0 0 18px;
  color: rgba(255, 255, 255, 0.78);
  line-height: 1.8;
}

.contact-section {
  padding-top: 120px;
  padding-bottom: 120px;
}

.contact-card {
  border: 1px solid rgba(255, 255, 255, 0.08);
  background: rgba(255, 255, 255, 0.03);
  border-radius: 28px;
  padding: 44px 48px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.contact-card h2 {
  margin: 0 0 12px;
  font-size: clamp(3rem, 6vw, 4rem);
}

.contact-card p {
  margin: 0;
  color: rgba(255, 255, 255, 0.75);
}

.footer {
  padding: 28px 40px;
  text-align: center;
  color: rgba(255, 255, 255, 0.55);
}

@media (max-width: 1120px) {
  .project-grid,
  .testimonial-grid,
  .faq-grid,
  .about-grid,
  .hero-top {
    grid-template-columns: 1fr;
  }

  .project-card-large,
  .project-card-small,
  .about-image,
  .hero-image {
    min-height: 300px;
  }
}

@media (max-width: 820px) {
  .nav-container {
    flex-wrap: wrap;
    justify-content: center;
  }

  .nav-links,
  .nav-button {
    width: 100%;
    text-align: center;
  }

  .nav-links {
    justify-content: center;
  }

  .section {
    padding: 60px 24px;
  }

  .contact-card {
    flex-direction: column;
    gap: 18px;
    text-align: center;
  }
}

@media (max-width: 560px) {
  .hero-brand {
    font-size: 7rem;
  }

  .hero-copy h1 {
    font-size: 3.8rem;
  }

  .section-header,
  .section-top-row {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>