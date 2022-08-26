<script lang="jsx">
import { defineComponent } from 'vue'
import Todo from './components/Todo.vue'

import './assets/base.css'

const App = defineComponent({
  name: 'App',
  render() {
    return (
      <div>
        <Todo />
      </div>
    )
  }
})

export default App
</script>