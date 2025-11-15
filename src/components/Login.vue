<template>
  <div class="min-h-screen flex items-center justify-center bg-gray-100">
    <div class="bg-white p-8 rounded-xl shadow-lg w-96">
      <h2 class="text-2xl font-bold mb-6 text-center text-gray-800">Вход в аккаунт</h2>
      
      <form @submit.prevent="handleLogin" class="space-y-4">
        <div>
          <label for="email" class="block text-gray-700 mb-1">Email</label>
          <input
            type="email"
            id="email"
            v-model="email"
            placeholder="Введите email"
            required
            class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent"
          />
        </div>

        <div>
          <label for="password" class="block text-gray-700 mb-1">Пароль</label>
          <input
            type="password"
            id="password"
            v-model="password"
            placeholder="Введите пароль"
            required
            class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-green-500 focus:border-transparent"
          />
        </div>

        <button
          type="submit"
          @click="login"
          class="w-full bg-green-500 text-white py-2 rounded-lg hover:bg-green-600 transition-colors"
        >
          Войти
        </button>

        <p v-if="errorMessage" class="text-red-500 text-sm mt-2 text-center">{{ errorMessage }}</p>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      email: "",
      password: "",
      errorMessage: "",
    };
  },
  methods: {
    handleLogin() {
      if (!this.email || !this.password) {
        this.errorMessage = "Все поля должны быть заполнены";
        return;
      }

      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailPattern.test(this.email)) {
        this.errorMessage = "Введите корректный email";
        return;
      }

      this.errorMessage = "";

      // Сохраняем userId
      localStorage.setItem('userId', this.email);

      // Перезагружаем страницу, чтобы сработал navigation guard
      window.location.reload();
    },
  },
};
</script>
