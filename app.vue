<template>
  <div class="absolute inset-0 w-full h-full flex justify-center items-center">
    <div class="card shadow-lg rounded p-4 w-1/3">
      <dynamic-form :form="form" />
    </div>
  </div>
</template>

<script>
import { defineComponent } from "@vue/composition-api";
import { TextField, PasswordField } from "@asigloo/vue-dynamic-forms";

export default defineComponent({
  setup() {
    const form = reactive({
      id: "test-form",
      fields: {
        username: TextField({
          label: "Username",
          name: "username",
          value: "",
          validators: [
            {
              type: "required",
              message: "Username is required",
            },
          ],
        }),
        password: PasswordField({
          label: "Password",
          name: "password",
          value: "",
          validators: [
            {
              type: "required",
              message: "Password is required",
            },
          ],
        }),
      },
    });

    return {
      form,
    };
  },
});
</script>

<style>
.form-group {
  @apply flex flex-col mb-4;
}

.form-label {
  @apply w-full mb-3 text-sm font-bold;
}
.form-control {
  @apply border-2 border-gray-300 rounded-lg px-4 py-2;

}
.form-control:focus{
  @apply outline-none border-green-400;
}
.form-control--success{
  @apply border-green-400 bg-green-50;
}
.form-control--error {
  @apply border-red-400 bg-red-50
}
.form-hint{
  @apply text-sm
}
.form-error{
  @apply text-red-500
}
.checkbox-control,
.radio-control
{
  @apply mr-4
  
}
.checkbox-control,
.radio-control
{
  @apply select-none cursor-pointer text-sm;
  
}


</style>
