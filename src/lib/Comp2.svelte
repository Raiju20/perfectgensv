<!-- Comp2.svelte -->
<script>
    import Value2 from './Value2.svelte';
  
    let button;
  
    function handleClick() {
      alert('Кнопка в Comp2 нажата!');
    }
  </script>
  
  <button bind:this={button} on:click={handleClick}>
    Нажми меня в Comp2
  </button>
  
  <Value2 {button} /> <!-- Передаем button как пропс -->