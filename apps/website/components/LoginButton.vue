<script lang="ts" setup>
import { LogIn } from 'lucide-vue-next'
import { computed, ref } from 'vue'

const email = ref('')
const verificationCode = ref('')
const isSending = ref(false)
const countdown = ref(0)

const isEmailValid = computed(() => {
  return /^[^\s@]+@[^\s@][^\s.@]*\.[^\s@]+$/.test(email.value)
})

const canSubmit = computed(() => {
  return isEmailValid.value && verificationCode.value.length === 6
})

const sendButtonText = computed(() => {
  if (countdown.value > 0)
    return `${countdown.value} seconds later`
  return isSending.value ? 'Sending...' : 'Send verification code'
})

function startCountdown() {
  countdown.value = 60
  const timer = setInterval(() => {
    countdown.value--
    if (countdown.value <= 0) {
      clearInterval(timer)
      isSending.value = false
    }
  }, 1000)
}

async function sendVerificationCode() {
  if (!isEmailValid.value || isSending.value)
    return

  isSending.value = true
  try {
    // TODO: 调用发送验证码API
    await new Promise(resolve => setTimeout(resolve, 1000))
    startCountdown()
  }
  catch (error) {
    console.error('发送验证码失败:', error)
  }
}

async function loginWithGoogle() {
  // TODO: 实现Google登录
}

async function loginWithGithub() {
  // TODO: 实现Github登录
}

async function handleLogin() {
  if (!canSubmit.value)
    return

  try {
    // TODO: 实现邮箱验证码登录
  }
  catch (error) {
    console.error('登录失败:', error)
  }
}
</script>

<template>
  <Dialog>
    <DialogTrigger as-child>
      <Button class="gap-2">
        <LogIn class="h-5 w-5" />
        <span>Login</span>
      </Button>
    </DialogTrigger>
    <DialogContent class="sm:max-w-[425px]">
      <DialogHeader>
        <DialogTitle>Login</DialogTitle>
        <DialogDescription>
          Choose one of the following ways to login
        </DialogDescription>
      </DialogHeader>
      <div class="flex flex-col gap-4 py-4">
        <Button variant="outline" class="gap-2" @click="loginWithGoogle">
          <Icon name="devicon:google" class="size-5" />
          Continue with Google
        </Button>
        <Button variant="outline" class="gap-2" @click="loginWithGithub">
          <Icon name="devicon:github" class="size-5 block dark:hidden" />
          <Icon name="mdi:github" class="size-5 hidden hidden dark:block" />
          Continue with Github
        </Button>
        <div class="relative">
          <div class="absolute inset-0 flex items-center">
            <span class="w-full border-t" />
          </div>
          <div class="relative flex justify-center text-xs uppercase">
            <span class="bg-background px-2 text-muted-foreground">Or use email to login</span>
          </div>
        </div>
        <div class="space-y-4">
          <div class="space-y-2">
            <Input v-model="email" type="email" placeholder="Enter your email" />
          </div>
          <div class="flex items-center gap-2">
            <Input v-model="verificationCode" placeholder="Verification code" />
            <Button
              variant="outline"
              :disabled="!isEmailValid || isSending"
              @click="sendVerificationCode"
            >
              {{ sendButtonText }}
            </Button>
          </div>
        </div>
      </div>
      <DialogFooter>
        <Button type="submit" :disabled="!canSubmit" @click="handleLogin">
          Login
        </Button>
      </DialogFooter>
    </DialogContent>
  </Dialog>
</template>
