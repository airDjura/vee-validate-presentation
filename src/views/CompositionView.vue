<template>
<div class="columns">
  <div class="column"></div>
  <div class="column is-6">
    <Form @submit="onSubmit" :validation-schema="schema">
      <div class="field">
        <label class="label">Email</label>
        <div class="control">
          <input class="input" :class="{'is-danger': emailError}" name="email" v-model="email" />
        </div >
        <p v-if="emailError" class="help is-danger">{{ emailError }}</p>
      </div>
      <div class="field">
        <label class="label">Password</label>
        <div class="control">
          <input class="input" :class="{'is-danger': passwordError}" name="password" v-model="password" type="password" />
        </div>
        <p v-if="passwordError" class="help is-danger">{{ passwordError }}</p>
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
  <div>

  </div>
</template>
<script>
import { useForm, useField } from 'vee-validate'
export default {
  setup () {
    // Define a validation schema
    const schema = {
      email: 'required|email'
    }
    // Create a form context with the validation schema
    const { handleSubmit } = useForm({
      validationSchema: schema
    })
    // No need to define rules for fields
    const { value: email, errorMessage: emailError } = useField('email')
    const { value: password, errorMessage: passwordError } = useField('password')

    const onSubmit = handleSubmit(values => {
      alert(JSON.stringify(values, null, 2))
    })

    return {
      onSubmit,
      email,
      emailError,
      password,
      passwordError
    }
  }
}
</script>
