<script lang="jsx">
import { defineComponent, reactive } from 'vue'

import styles from '../assets/Main.module.css'

const Todo = defineComponent({
  name: 'Todo',
  setup() {
    const state  = reactive({
      items: [
        { id: 0, task: 'Tarefa de teste' }
        /*{ id: 0, task: 'studing Vue JSX' },
        { id: 1, task: 'studing Vue Setup' }*/
      ],
      newItem: ''
    })

    function handleSetNewItem(e) {
      state.newItem = e.target.value
    }

    function handleAddToList() {
      if (state.newItem !== '') {
        state.items.push({
          task: state.newItem
        })
        state.newItem = ''
      }  
    }

    return {
      state,
      handleSetNewItem,
      handleAddToList,
    }
  },
  render () {
    return (
      <div className={styles.container}> 
        <div className={styles.box_input}>
          <input 
            type="text" 
            placeholder="Digite uma tarefa" 
            onChange={this.handleSetNewItem}
          />
          <button onClick={this.handleAddToList}>Enter a Task</button>
        </div>
        <div className={styles.box_tasks}>
          <ul>
            {
              this.state.items.map((item, id) => (
                <li key={id} className={styles.list_item}>{item.task}</li>
              ))
            }
          </ul>
        </div>
      </div>
    )
  }
})

export default Todo
</script>