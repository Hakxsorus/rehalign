<script setup lang="ts">
import ServiceCard from '@/components/ServiceCard.vue';
import WestMidlandsMap from '@/components/WestMidlandsMap.vue';
import { computed, onMounted, onUnmounted, ref } from 'vue';

const links = ref([
  {
    label: 'Free Online Assessment',
    to: '/getting-started',
    icon: 'i-lucide-book-check'
  },
  {
    label: 'Book A Home Visit Now',
    to: '/getting-started/theme',
    color: 'neutral',
    variant: 'subtle',
    trailingIcon: 'i-lucide-arrow-right'
  }
])

const services = [
  {
    title: 'Neurological Rehabilitation',
    description:
      'Specialist physiotherapy for stroke, Parkinson’s, MS, neuropathy, Bell’s palsy, spinal cord and brain injuries, and cerebral palsy.',
    image:
      'https://images.unsplash.com/photo-1709880754438-b1fb5d2f074c?q=80&w=1470&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    badge: 'New',
    to: '/neurological-rehabilitation',
    icon: 'i-lucide-brain'
  },
  {
    title: 'Elderly & Geriatric Physiotherapy',
    description:
      'Maintain mobility, independence, and quality of life through arthritis care, posture training, and walking aid support.',
    image: 'https://images.pexels.com/photos/7551627/pexels-photo-7551627.jpeg',
    to: '/elderly-geriatric-physiotherapy',
    icon: 'i-lucide-users'
  },
  {
    title: 'Falls Prevention & Balance Training',
    description:
      'Reduce fall risk, improve stability, and build confidence with balance, vestibular, and coordination training.',
    image:
      'https://www.telecare24.co.uk/wp-content/uploads/2022/12/Elderly-Woman-Falling.jpg',
    to: '/falls-prevention-balance-training',
    icon: 'i-lucide-shield-check'
  },
  {
    title: 'Functional Rehabilitation',
    description:
      'Regain independence in daily tasks with sit-to-stand retraining, stair practice, and gait re-education.',
    image: 'https://images.pexels.com/photos/7446605/pexels-photo-7446605.jpeg',
    to: '/functional-rehabilitation',
    icon: 'i-lucide-activity'
  },
  {
    title: 'Post-Hospital & Post-Surgery Rehabilitation',
    description:
      'Safe recovery after illness, surgery, fractures, or deconditioning, including post-COVID rehabilitation.',
    image: 'https://images.pexels.com/photos/5473215/pexels-photo-5473215.jpeg',
    to: '/post-hospital-post-surgery-rehabilitation',
    icon: 'i-lucide-hospital'
  },
  {
    title: 'Orthopaedic Rehabilitation',
    description:
      'Rehabilitation after fractures, joint replacements, sports injuries, and musculoskeletal conditions.',
    image: 'https://images.pexels.com/photos/4506077/pexels-photo-4506077.jpeg',
    to: '/orthopaedic-rehabilitation',
    icon: 'i-lucide-bone'
  },
  {
    title: 'Respiratory Physiotherapy',
    description:
      'Breathing exercises, airway clearance, and chest physiotherapy for COPD, asthma, and post-pneumonia recovery.',
    image: 'https://images.pexels.com/photos/4056529/pexels-photo-4056529.jpeg',
    to: '/respiratory-physiotherapy',
    icon: 'i-lucide-wind'
  },
  {
    title: 'Paediatric Physiotherapy',
    description:
      'Support for children with developmental delays, cerebral palsy, post-injury recovery, and mobility challenges.',
    image: 'https://images.pexels.com/photos/8612923/pexels-photo-8612923.jpeg',
    to: '/paediatric-physiotherapy',
    icon: 'i-lucide-baby'
  },
  {
    title: 'Additional Services',
    description:
      'Tailored exercise plans, pain-relief techniques, caregiver guidance, and goal-based home rehab programs.',
    image: 'https://images.pexels.com/photos/4506078/pexels-photo-4506078.jpeg',
    to: '/additional-services',
    icon: 'i-lucide-plus-circle'
  }
]


const testimonials = [
  {
    user: {
      name: 'Sarah Thompson',
      description: 'Stroke Rehabilitation Patient',
      avatar: {
        src: 'https://randomuser.me/api/portraits/women/65.jpg',
        loading: 'lazy'
      }
    },
    quote:
      'The home physiotherapy sessions have been life-changing. I can walk confidently again thanks to their patience and expertise.'
  },
  {
    user: {
      name: 'David Miller',
      description: 'Hip Surgery Recovery',
      avatar: {
        src: 'https://randomuser.me/api/portraits/men/44.jpg',
        loading: 'lazy'
      }
    },
    quote:
      'Recovering from surgery at home with their guidance was the best decision I made. Professional, kind, and incredibly knowledgeable.'
  },
  {
    user: {
      name: 'Helen Parker',
      description: 'Parkinson’s Physiotherapy Client',
      avatar: {
        src: 'https://randomuser.me/api/portraits/women/72.jpg',
        loading: 'lazy'
      }
    },
    quote:
      'Their tailored exercises have improved my balance and mobility far beyond what I expected. Highly recommend to anyone seeking specialist care.'
  }
]

import type { StepperItem } from '@nuxt/ui'

const steps: StepperItem[] = [
  {
    title: 'Book an initial consultation',
    description: 'Choose a time online for a 60–75 min assessment.',
    icon: 'i-lucide-calendar-check'
  },
  {
    title: 'Home visit & assessment',
    description: 'Your physio visits and assesses movement, goals & risks.',
    icon: 'i-lucide-home'
  },
  {
    title: 'Choose a long-term plan',
    description: 'Get a tailored programme with schedule & tracking.',
    icon: 'i-lucide-clipboard-list'
  },
  {
    title: 'Rehabilitation & results',
    description: 'Progress reviews until you’re confident & independent.',
    icon: 'i-lucide-trophy'
  }
]

const active = ref(3)

const width = ref(window.innerWidth)

const updateWidth = () => {
  width.value = window.innerWidth
}

onMounted(() => {
  window.addEventListener('resize', updateWidth)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateWidth)
})

const orientation = computed(() => (width.value < 640 ? 'vertical' : 'horizontal'))



import type { FooterColumn } from '@nuxt/ui-pro'
import type { NavigationMenuItem } from '@nuxt/ui'

const footerColumns: FooterColumn[] = [
  {
    label: 'Services',
    children: [
      { label: 'Neurological Rehabilitation', to: '/neurological-rehabilitation' },
      { label: 'Elderly & Geriatric Physiotherapy', to: '/elderly-geriatric-physiotherapy' },
      { label: 'Falls Prevention & Balance Training', to: '/falls-prevention-balance-training' },
      { label: 'Post-Surgery Rehabilitation', to: '/post-hospital-post-surgery-rehabilitation' }
    ]
  },
  {
    label: 'Company',
    children: [
      { label: 'About Us', to: '/about' },
      { label: 'Areas We Cover', to: '/locations' },
      { label: 'Book a Home Visit', to: '/book' },
      { label: 'Contact', to: '/contact' }
    ]
  },
  {
    label: 'Resources',
    children: [
      { label: 'Blog', to: '/blog' },
      { label: 'Patient FAQs', to: '/faqs' },
      { label: 'Privacy Policy', to: '/privacy-policy' },
      { label: 'Terms & Conditions', to: '/terms' }
    ]
  }
]

const socialLinks: NavigationMenuItem[] = [
  { icon: 'i-simple-icons-facebook', to: 'https://facebook.com', target: '_blank', ariaLabel: 'Facebook' },
  { icon: 'i-simple-icons-instagram', to: 'https://instagram.com', target: '_blank', ariaLabel: 'Instagram' },
  { icon: 'i-simple-icons-linkedin', to: 'https://linkedin.com', target: '_blank', ariaLabel: 'LinkedIn' }
]

const faqItems = [
  {
    label: 'What areas do you cover?',
    icon: 'i-lucide-circle-help',
    content:
      'We cover most of the West Midlands (e.g., Birmingham, Solihull, Coventry, Wolverhampton, Walsall, Dudley, Sandwell) and are expanding. Check our full list on the Locations page.'
  },
  {
    label: 'Do you offer home visits?',
    icon: 'i-lucide-circle-help',
    content:
      'Yes — all sessions are delivered at your home or care setting, with equipment brought by your physiotherapist as needed.'
  },
  {
    label: 'How long is the first appointment?',
    icon: 'i-lucide-circle-help',
    content:
      'Initial consultations are typically 60–75 minutes to allow for assessment, goal setting, and a starter exercise plan.'
  },
  {
    label: 'What conditions do you treat?',
    icon: 'i-lucide-circle-help',
    content:
      'Neurological (stroke, Parkinson’s, MS), orthopaedic/post-surgery, elderly mobility and balance, respiratory rehab, paediatric cases, and more.'
  },
  {
    label: 'Do I need a GP referral?',
    icon: 'i-lucide-circle-help',
    content:
      'No referral required. You can book directly. We’re happy to liaise with your GP or consultant if helpful.'
  },
  {
    label: 'How many sessions will I need?',
    icon: 'i-lucide-circle-help',
    content:
      'It varies by condition and goals. Your physio will recommend a plan after the assessment and review progress regularly.'
  },
  {
    label: 'What should I wear and prepare?',
    icon: 'i-lucide-circle-help',
    content:
      'Wear comfortable clothing you can move in. Clear a small safe space if possible and have any mobility aids nearby.'
  },
  {
    label: 'Do you accept insurance or self-pay?',
    icon: 'i-lucide-circle-help',
    content:
      'We accept self-pay and can provide receipts for insurance claims where applicable. Contact us for details.'
  }
]

import { reactive } from 'vue'

const form = reactive({
  name: '',
  email: '',
  phone: '',
  message: ''
})
</script>

<template>
  <UPage>



    <section class="relative overflow-hidden">
      <!-- Background image -->
      <img src="../assets/clinic.jpg" alt="" class="absolute inset-0 h-full w-full object-cover" />

      <!-- Green tint -->
      <div class="absolute inset-0 bg-[#aeea00]/40 mix-blend-multiply"></div>

      <!-- Optional subtle gradient for text legibility -->
      <div class="absolute inset-0 bg-gradient-to-b from-black/25 to-black/5"></div>

      <!-- Hero content on top -->
      <UPageHero class="relative z-10 text-white" :ui="{
        title: 'text-white',
        description: 'text-white/90',
        links: 'flex flex-wrap gap-2' // reduce gap between buttons
      }" title="Rehabilitate & Realign Your Life"
        description="From recovery after injury to long-term mobility care — expert physiotherapy, delivered right to your door."
        headline="Expert Physiotherapy" orientation="horizontal" :links="links" />

    </section>

    <section class="py-8">
      <UPageCTA title=" Why Rehaligned?"
        description="Expert, home-based physiotherapy—personalised plans, evidence-led care, and flexible scheduling that fits your life."
        orientation="horizontal" variant="naked" :links="[
          { label: 'Book A Home Visit', color: 'primary', size: 'lg', to: '/book', icon: 'i-lucide-home' },
          { label: 'Our Services', color: 'neutral', variant: 'subtle', trailingIcon: 'i-lucide-arrow-right', to: '/services' }
        ]" :ui="{ links: 'flex flex-wrap gap-x-2 gap-y-2' }" class="rounded-none sm:rounded-xl">
        <!-- Illustration -->
        <img src="https://images.pexels.com/photos/5473177/pexels-photo-5473177.jpeg"
          alt="Physiotherapist supporting patient at home" class="w-full rounded-lg" loading="lazy" />

        <!-- Features list using UPageFeature -->
        <template #body>
          <div class="mt-6 grid gap-4 sm:grid-cols-2">
            <UPageFeature icon="i-lucide-user-check" title="Fully Qualified"
              description="UK-trained physiotherapists with proven expertise." orientation="horizontal" />
            <UPageFeature icon="i-lucide-home" title="Home Visits"
              description="Serving patients across the West Midlands." orientation="horizontal" />
            <UPageFeature icon="i-lucide-clipboard-list" title="Tailored Plans"
              description="Rehab programmes built around your needs." orientation="horizontal" />
            <UPageFeature icon="i-lucide-heart-pulse" title="Surgery & Injury Recovery"
              description="Safe, progressive recovery support." orientation="horizontal" />
            <UPageFeature icon="i-lucide-brain" title="Neuro & Elderly Care"
              description="Specialist mobility and function therapy." orientation="horizontal" />
            <UPageFeature icon="i-lucide-bar-chart-2" title="Progress Tracking"
              description="Regular reviews to keep you improving." orientation="horizontal" />
          </div>

        </template>
      </UPageCTA>
    </section>

    <section class="py-8 bg-gray-50">
      <UContainer>
        <h2 class="text-4xl font-bold text-center mb-2">Our Services</h2>
        <p class="text-center text-gray-600 mb-6">
          Comprehensive physiotherapy services addressing the UK’s most common conditions
        </p>
        <UPageGrid class="gap-4">
          <UPageCard v-for="s in services" :key="s.to" :title="s.title" :description="s.description" :icon="s.icon"
            :to="s.to" variant="subtle" spotlight>
            <img :src="s.image" :alt="s.title" class="w-full h-40 object-cover rounded-md" />
          </UPageCard>
        </UPageGrid>
        <div class="flex justify-center pt-8">
          <UButton to="/services" size="xl" trailingIcon='i-lucide-arrow-right'>Explore More Services</UButton>
        </div>
      </UContainer>
    </section>
    <!-- <UPageSection class="bg-primary-50" title="Testimonials"
      description=" We're trusted by our patients to deliver expert care and lasting results.">
      <UPageMarquee :overlay="false" :ui="{ root: '[--gap:--spacing(4)]', content: 'w-auto py-1' }">
        <UPageCard v-for="(testimonial, index) in testimonials" :key="index" variant="outline"
          :description="testimonial.quote" :ui="{
            description: 'before:content-[open-quote] after:content-[close-quote] line-clamp-3'
          }" class="w-64 shrink-0">
          <template #footer>
            <UUser v-bind="testimonial.user" size="xl" :ui="{ description: 'line-clamp-1' }" />
          </template>
</UPageCard>
</UPageMarquee>
</UPageSection> -->
    <section class="py-8 bg-primary-50">
      <UContainer>
        <h2 class="text-4xl font-bold text-center mb-2">Testimonials</h2>
        <p class="text-center text-gray-600 mb-6">
          We're trusted by our patients to deliver expert care and lasting results.
        </p>
      </UContainer>
      <UPageMarquee :overlay="false" :ui="{ root: '[--gap:--spacing(4)]', content: 'w-auto py-1' }">
        <UPageCard v-for="(testimonial, index) in testimonials" :key="index" variant="outline"
          :description="testimonial.quote" :ui="{
            description: 'before:content-[open-quote] after:content-[close-quote] line-clamp-3'
          }" class="w-64 shrink-0">
          <template #footer>
            <UUser v-bind="testimonial.user" size="xl" :ui="{ description: 'line-clamp-1' }" />
          </template>
        </UPageCard>
      </UPageMarquee>
    </section>


    <section class="py-8">
      <UPageCTA title="Areas We Cover" description="Home physiotherapy across the West Midlands — and we’re expanding."
        orientation="horizontal" variant="naked" :links="[
          { label: 'Book A Home Visit', color: 'primary', size: 'lg', to: '/book', icon: 'i-lucide-home' },
          { label: 'All Locations', color: 'neutral', variant: 'subtle', trailingIcon: 'i-lucide-arrow-right', to: '/locations' }
        ]" :ui="{ links: 'flex flex-wrap gap-x-2 gap-y-2' }" class="rounded-none sm:rounded-xl bg-white">
        <!-- Map beside text -->
        <WestMidlandsMap class="w-full rounded-lg overflow-hidden ring ring-default" />

        <!-- Locations list under the description -->
        <template #body>
          <div class="mt-6 grid gap-2">
            <UPageFeature icon="i-lucide-map-pin" title="Birmingham" description="City & suburbs" />
            <UPageFeature icon="i-lucide-map-pin" title="Solihull" description="Including Shirley & Knowle" />
            <UPageFeature icon="i-lucide-map-pin" title="Coventry" description="All major districts" />
            <UPageFeature icon="i-lucide-map-pin" title="Wolverhampton" description="Wider Black Country" />
          </div>
        </template>
      </UPageCTA>
    </section>

    <section class="py-16 bg-gray-50">
      <UContainer>
        <h2 class="text-4xl font-bold text-center mb-2">Your Journey With Us</h2>
        <p class="text-center text-gray-600 mb-12">
          From your first consultation to full recovery, we’re with you every step of the way.
        </p>

        <div class="flex justify-center">
          <UStepper :items="steps" :orientation="orientation" size="lg" class="w-full max-w-5xl" v-model="active" />
        </div>
      </UContainer>
    </section>

    <section class="py-8">
      <UContainer>
        <UPageCTA title="Common Questions"
          description="Answers to the queries we hear most from patients, giving you a clear picture of how we work, what to expect at each stage of your recovery, and the standards of care we uphold."
          orientation="horizontal" variant="naked" :links="[
            { label: 'Book A Home Visit', color: 'primary', size: 'lg', to: '/book', icon: 'i-lucide-home' },
            { label: 'Contact Us', color: 'neutral', variant: 'subtle', trailingIcon: 'i-lucide-arrow-right', to: '/contact' }
          ]" :ui="{ links: 'flex flex-wrap gap-x-2 gap-y-2' }" class="rounded-none sm:rounded-xl bg-white">
          <!-- Right side: Accordion -->
          <div class="w-full">
            <UPageAccordion :items="faqItems" type="single" default-value="0" />
          </div>
        </UPageCTA>
      </UContainer>
    </section>

    <section class="py-16 bg-primary-50">
      <UContainer>
        <h2 class="text-4xl font-bold text-center mb-2">Contact Us</h2>
        <p class="text-center text-gray-600 mb-8">
          Have questions or ready to book your home visit? Our friendly team is here to help.
        </p>

        <div class="flex flex-col gap-3 max-w-lg mx-auto justify-center w-full">
          <UButton label="Book A Home Visit" color="primary" size="lg" to="/book" class="w-full" variant="subtle"
            icon="i-lucide-home" />
          <UButton label="Message us on WhatsApp" color="neutral" variant="subtle" size="lg"
            icon="i-lucide-message-circle" to="/" target="_blank" class="w-full" />
          <UCard class="w-full">
            <form @submit.prevent>
              <div class="grid gap-4">
                <UFormField name="name" label="Full name">
                  <UInput v-model="form.name" placeholder="Jane Doe" class="w-full" />
                </UFormField>

                <UFormField name="email" label="Email address">
                  <UInput v-model="form.email" type="email" placeholder="you@example.com" class="w-full" />
                </UFormField>

                <UFormField name="phone" label="Phone (optional)">
                  <UInput v-model="form.phone" type="tel" placeholder="+44 7xxx xxx xxx" class="w-full" />
                </UFormField>

                <UFormField name="message" label="How can we help?">
                  <UTextarea v-model="form.message" placeholder="Tell us a little about your needs…" class="w-full" />
                </UFormField>
              </div>

              <UButton type="submit" color="primary" class="mt-4 cursor-pointer" icon="i-lucide-send">
                Send Message
              </UButton>
            </form>
          </UCard>
        </div>
      </UContainer>
    </section>




    <UFooter class="bg-gray-200 border-t border-gray-200 py-4">
      <!-- Top: logo + columns -->
      <template #top>
        <UContainer>
          <UFooterColumns :columns="footerColumns" class="items-center">
            <!-- Left: Logo -->
            <template #left>
              <div class="flex justify-center sm:justify-start">
                <img src="../assets/Logo-NoText.png" alt="Rehaligned Logo" class="h-16 w-auto" loading="lazy" />
                <!-- Smaller height -->
              </div>
            </template>
          </UFooterColumns>
        </UContainer>
      </template>

      <!-- Bottom: copyright + socials -->
      <template #bottom>
        <UContainer class="flex flex-col sm:flex-row items-center justify-between gap-2 py-2">
          <p class="text-muted text-sm text-center sm:text-left">
            © {{ new Date().getFullYear() }} Rehaligned Ltd. All rights reserved.
          </p>
          <div class="flex gap-1">
            <UButton v-for="link in socialLinks" :key="link.icon" :icon="link.icon" color="neutral" variant="ghost"
              :to="link.to" :target="link.target" :aria-label="link.ariaLabel" />
          </div>
        </UContainer>
      </template>
    </UFooter>



  </UPage>
</template>
