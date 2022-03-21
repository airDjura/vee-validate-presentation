<template>
<div class="columns">
  <div class="column"></div>
  <div class="column is-6">
    <Form @submit="onSubmit" :validation-schema="schema">
    <div class="field">
      <p class="control has-icons-left has-icons-right">
        <Field class="input" name="email" type="email" placeholder="Email" />
        <ErrorMessage name="email" />
      </p>
    </div>
    <div class="field">
      <p class="control has-icons-left">
        <Field class="input" name="password" type="password" placeholder="Password" />
        <ErrorMessage name="password" />
      </p>
    </div>
    <div class="field">
      <p class="control">
        <button class="button is-success">
          Login
        </button>
      </p>
    </div>
    </Form>
  </div>
  <div class="column"></div>
</div>

</template>
<script>
import { Form, Field, ErrorMessage } from 'vee-validate'
import * as yup from 'yup'
export default {
  components: {
    Form,
    Field,
    ErrorMessage
  },
  data () {
    const schema = yup.object({
      email: yup.string().required().email(),
      password: yup.string().required().min(8)
    })
    return {
      schema
    }
  },
  methods: {
    onSubmit (values) {
      // Submit values to API...
      alert(JSON.stringify(values, null, 2))
    }
  }
}
</script>
