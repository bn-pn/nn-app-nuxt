<template>
  <div>
    <h1 class="title">会社情報</h1>
    <form>
      <div class="form-group">
        <label>会社名*</label>
        <input
          type="text"
          class="form-control"
          v-model="$v.form.company.$model"
        />
        <div class="text-danger" v-if="$v.form.company.$error">
          会社名は必須です
        </div>
      </div>
      <div class="form-group">
        <label>氏名*</label>
        <input type="text" class="form-control" v-model="$v.form.name.$model" />
        <div class="text-danger" v-if="$v.form.name.$error">
          氏名は必須です
        </div>
      </div>
      <div class="form-group">
        <label>住所*</label>
        <input
          type="text"
          class="form-control"
          v-model="$v.form.address.$model"
        />
        <div class="text-danger" v-if="$v.form.address.$error">
          住所は必須です
        </div>
      </div>
      <button type="submit" class="btn btn-primary" @click.prevent="submit">
        登録
      </button>
    </form>
  </div>
</template>

<script>
import { required } from "vuelidate/lib/validators";

export default {
  name: "FormPage",
  data() {
    return {
      form: {
        company: "",
        name: "",
        address: "",
      },
    };
  },
  methods: {
    submit() {
      this.$v.$touch();
      if (this.$v.$invalid) {
        console.log("バリデーションエラー");
      } else {
        alert('登録完了');
      }
    },
  },
  validations: {
    form: {
      company: { required },
      name: { required },
      address: { required },
    },
  },
};
</script>
