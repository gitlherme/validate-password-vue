<template>
  <div class="password-validate">
    <h1><i class="fas fa-shield-alt"></i>Validador de força da senha</h1>
    <label for="password">Digite uma senha abaixo</label>
    <input
      type="password"
      name="password"
      id="password"
      v-model="password"
      placeholder="Digite uma senha..."
    />
    <div class="validate-criteria">
      <span :class="hasMinimumLength ? 'checked' : 'not-checked'"
        ><i :class="hasMinimumLength ? 'fas fa-check' : 'fas fa-times'"></i
        >Possui ao menos 8 caracteres</span
      >
      <span :class="hasLowercase ? 'checked' : 'not-checked'"
        ><i :class="hasLowercase ? 'fas fa-check' : 'fas fa-times'"></i>Possui
        ao menos uma letra minúscula</span
      >
      <span :class="hasUppercase ? 'checked' : 'not-checked'"
        ><i :class="hasUppercase ? 'fas fa-check' : 'fas fa-times'"></i>Possui
        ao menos uma letra maiúscula</span
      >
      <span :class="hasNumber ? 'checked' : 'not-checked'"
        ><i :class="hasNumber ? 'fas fa-check' : 'fas fa-times'"></i>Possui ao
        menos um número</span
      >
      <span :class="hasEspecial ? 'checked' : 'not-checked'"
        ><i :class="hasEspecial ? 'fas fa-check' : 'fas fa-times'"></i>Possui ao
        menos um caractere especial</span
      >
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  data() {
    return {
      password: "",
      hasMinimumLength: false,
      hasLowercase: false,
      hasUppercase: false,
      hasNumber: false,
      hasEspecial: false,
    };
  },
  watch: {
    password() {
      // Criando as Regex
      this.hasMinimumLength = this.password.length >= 8;
      this.hasLowercase = /[a-z]/.test(this.password);
      this.hasUppercase = /[A-Z]/.test(this.password);
      this.hasNumber = /[0-9]/.test(this.password);
      this.hasEspecial = /[@!#$%^&*()/\\]/.test(this.password);
    },
  },
});
</script>

<style scoped>
h1,
span,
label {
  font-family: "Inter";
  color: #fff;
}

h1 {
  font-weight: 900;
  margin: 48px 0px;
}

i {
  margin-right: 10px;
}

span {
  font-weight: 300;
  margin: 16px 0px;
}

label {
  font-weight: 600;
}

input {
  margin: 32px 0px;
  width: 100%;
  padding: 16px 8px;
  border: none;
}

.checked {
  color: green;
}

.validate-criteria {
  display: flex;
  flex-direction: column;
}
</style>
