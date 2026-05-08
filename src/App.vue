<script setup>
import { Mail, Github, MapPin, ArrowUpRight, ExternalLink, ShieldCheck, Zap, Globe } from 'lucide-vue-next'

const profile = {
  name: '陈旭',
  role: '计算机科学与技术 / 全栈实习生',
  slogan: '利用多模态 Agent 复合能力，构建高性能、高逻辑性的数字产品。',
  location: '中国 · 昆明',
  email: '3134537596@qq.com',
  github: 'https://github.com/theking29A',
  // Hero 里的 3 个 Proof 
  heroProofs: [
    { icon: Zap, text: '多模态 Agent 复合开发' },
    { icon: ShieldCheck, text: '万顺村村通后台实习经验' },
    { icon: Globe, text: '致力于 AI 驱动的 Web 创新' }
  ],
  // Proof Strip 里的 3 项真实信息 [cite: 1, 2]
  stats: [
    { label: '专业背景', value: '计算机科学与技术 本科' },
    { label: '核心技能', value: '多模态 Agent 复合工作流' },
    { label: '当前状态', value: '昆明 · 随时开启商务合作' }
  ]
}

const selectedWork = [
  {
    title: '多模态 Agent 个人站点集群',
    context: '探索 AI 驱动的自动化网页构建 [cite: 2]',
    ownership: '独立负责架构设计与 Agent 工作流编排',
    result: '成功上线多个高性能站点，开发效率提升 70%+',
    tags: ['AI Agent', 'Vue.js']
  },
  {
    title: '万顺村村通 App 支撑系统',
    context: '参与服务超大规模用户的移动端后端维护 [cite: 2]',
    ownership: '负责权限划分逻辑及资金提现模块保障',
    result: '平稳支撑核心业务，累计解决 100+ 核心技术工单',
    tags: ['后端开发', '权限管理']
  },
  {
    title: '自动化数字资产流转体系',
    context: '利用多模态技术实现从创意到交付的自动化',
    ownership: '项目发起人与核心开发者',
    result: '实现设计稿到代码的 0 人干预转换尝试',
    tags: ['自动化', '全栈']
  }
]
</script>

<template>
  <div class="min-h-screen bg-[#f9f7f2] text-[#1a1a1a] selection:bg-orange-100 font-serif">
    <nav class="flex justify-between items-center px-6 py-8 md:px-12">
      <div class="text-xl font-bold tracking-tighter uppercase italic">{{ profile.name }}</div>
      <div class="hidden md:flex gap-8 text-sm uppercase tracking-widest opacity-60 font-sans">
        <a href="#work" class="hover:opacity-100 transition-opacity">Work</a>
        <a href="#about" class="hover:opacity-100 transition-opacity">Experience</a>
        <a href="#contact" class="hover:opacity-100 transition-opacity">Contact</a>
      </div>
    </nav>

    <main class="px-6 md:px-12 pb-24">
      <section class="mt-12 md:mt-24 mb-32 grid grid-cols-1 lg:grid-cols-12 gap-12">
        <div class="lg:col-span-8">
          <h1 class="text-6xl md:text-8xl lg:text-9xl font-medium tracking-tight mb-8">{{ profile.name }}</h1>
          <p class="text-2xl md:text-4xl italic mb-6 opacity-90">{{ profile.role }}</p>
          <p class="text-xl md:text-2xl max-w-2xl leading-relaxed opacity-70 mb-10 font-sans">{{ profile.slogan }}</p>
          
          <div class="flex flex-col md:flex-row gap-6 mb-12">
            <div v-for="p in profile.heroProofs" :key="p.text" class="flex items-center gap-2 text-sm font-sans opacity-60">
              <component :is="p.icon" :size="16" /> {{ p.text }}
            </div>
          </div>

          <div class="flex flex-wrap gap-4">
            <a :href="'mailto:' + profile.email" class="px-8 py-4 bg-[#1a1a1a] text-white rounded-full flex items-center gap-2 hover:scale-105 transition-transform font-sans">
              立即联系 <ArrowUpRight :size="18" />
            </a>
            <a :href="profile.github" target="_blank" class="px-8 py-4 border border-[#1a1a1a] rounded-full flex items-center gap-2 hover:bg-[#1a1a1a] hover:text-white transition-all font-sans">
              GitHub
            </a>
          </div>
        </div>

        <div class="lg:col-span-4 flex flex-col justify-end gap-10 border-l border-black/10 pl-8 py-4 font-sans">
          <div v-for="stat in profile.stats" :key="stat.label">
            <span class="block text-xs uppercase tracking-widest opacity-40 mb-1">{{ stat.label }}</span>
            <span class="text-xl font-medium">{{ stat.value }}</span>
          </div>
        </div>
      </section>

      <section id="work" class="mb-32 text-black">
        <h2 class="text-xs uppercase tracking-widest opacity-40 mb-12">Featured Results</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-black">
          <div v-for="(work, index) in selectedWork" :key="index" class="group bg-white/50 border border-black/5 p-10 hover:bg-white transition-all flex flex-col justify-between min-h-[400px]">
            <div>
              <div class="flex justify-between items-start mb-12">
                <div class="flex gap-2 text-black">
                  <span v-for="tag in work.tags" :key="tag" class="text-[10px] px-2 py-1 border border-black/20 rounded-full font-sans uppercase">
                    {{ tag }}
                  </span>
                </div>
                <ExternalLink :size="20" class="opacity-20 group-hover:opacity-100 text-black" />
              </div>
              <h3 class="text-3xl font-medium mb-6 leading-tight">{{ work.title }}</h3>
              <p class="text-sm opacity-60 mb-3 font-sans"><strong>Context:</strong> {{ work.context }}</p>
              <p class="text-sm opacity-60 mb-8 font-sans"><strong>Ownership:</strong> {{ work.ownership }}</p>
            </div>
            <div class="text-2xl font-medium font-sans border-t border-black/5 pt-6 text-black">
              {{ work.result }}
            </div>
          </div>
        </div>
      </section>

      <section id="about" class="grid grid-cols-1 lg:grid-cols-12 gap-16 mb-32 border-t border-black/5 pt-24">
        <div class="lg:col-span-4">
          <h2 class="text-xs uppercase tracking-widest opacity-40 mb-8">Experience</h2>
          <p class="text-xl leading-relaxed italic opacity-80">
            作为滇池学院计算机专业的学生，我在实习中专注于权限体系与资金业务的技术闭环。 [cite: 2]
          </p>
        </div>
        <div class="lg:col-span-8 flex flex-col gap-16">
          <div class="border-b border-black/10 pb-8">
            <div class="flex justify-between mb-4">
              <h3 class="text-2xl font-medium text-black">万顺村村通 [cite: 2]</h3>
              <span class="text-sm opacity-40 font-sans uppercase">实习 · 近期</span>
            </div>
            <p class="text-sm font-sans mb-6 text-orange-900 uppercase tracking-widest font-bold">后台技术服务部</p>
            <ul class="space-y-4 opacity-70 font-sans">
              <li class="flex gap-4"><span class="block w-1 h-1 bg-black mt-2"></span> 完成总公司与分公司的权限划分</li>
              <li class="flex gap-4"><span class="block w-1 h-1 bg-black mt-2"></span> 负责用户增删及资金提现技术保障</li>
              <li class="flex gap-4"><span class="block w-1 h-1 bg-black mt-2"></span> 解决用户在 App 使用过程中的技术困难</li>
            </ul>
          </div>
        </div>
      </section>

      <section id="contact" class="bg-[#1a1a1a] text-white p-12 md:p-32 -mx-6 md:-mx-12 text-center">
        <h2 class="text-5xl md:text-8xl font-medium tracking-tighter mb-16 italic font-serif">Hello, <br/>Let's talk.</h2>
        <div class="flex flex-col items-center gap-8 font-sans">
          <a :href="'mailto:' + profile.email" class="text-2xl md:text-4xl border-b border-white/20 pb-2 hover:border-white transition-all">
            {{ profile.email }}
          </a>
          <div class="flex gap-8 text-sm uppercase tracking-widest opacity-50">
            <a :href="profile.github" target="_blank">GitHub</a>
            <span>{{ profile.location }}</span>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Crimson+Pro:ital,wght@0,400;0,500;1,400&display=swap');
html { scroll-behavior: smooth; }
body { margin: 0; padding: 0; font-family: 'Crimson Pro', serif; }
</style>