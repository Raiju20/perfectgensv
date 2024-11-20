<!-- Value2.svelte -->
<script>
    export let button;
  
    // Функция для изменения стиля кнопки
    function changeButtonStyle() {
      if (button) {
        button.style.backgroundColor = 'green'; // Изменяем цвет кнопки
        button.style.color = 'white'; // Изменяем цвет текста
      }
    }
  
    // Вызываем функцию при монтировании компонента
    import { onMount } from 'svelte';
    
    onMount(() => {
      changeButtonStyle();
    });
  </script>
  
  <p>Кнопка будет изменена в Value2 компоненте.</p>