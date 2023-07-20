## Validação de Eventos {#events-validation}

Semelhante à validação de tipos de propriedades, um evento emitido pode ser validado se for definido com a sintaxe de objeto em vez da sintaxe de array.

Para adicionar validação, o evento é atribuído a uma função que recebe os argumentos passados para a chamada <span class="options-api">`this.$emit`</span><span class="composition-api">`emit`</span> e retorna um booleano para indicar se o evento é válido ou não.

<div class="composition-api">

```vue
<script setup>
const emit = defineEmits({
  // Sem validação
  click: null,

  // Validar evento submit
  submit: ({ email, password }) => {
    if (email && password) {
      return true
    } else {
      console.warn('Carga útil do evento submit inválida!')
      return false
    }
  }
})

function submitForm(email, password) {
  emit('submit', { email, password })
}
</script>

