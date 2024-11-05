<script>
    let props = $props();
  
    // Вызывается при изменении любого props'a
    // и обновляет значения массива для распечатки стиля
    $effect(() => {
      stl.display = props.selected.disp;
      stl["flex-direction"] = props.selected.direct;
      stl["justify-content"] = props.selected.just_content;
    });
  
    // Объект для распечатки стиля с умолчаниями
    let stl = $state({
      display: "block",
      "flex-direction": "row",
      "justify-content": "flex-start",
    });
  
    // Имя класса для распечатки стиля
    let class_name = ".flex-class {";
  </script>
  
  <div
    class="container"
    style="--disp:{props.selected.disp};
           --direct:{props.selected.direct};
           --justcont:{props.selected.just_content}"
  >
    <div class="flex-show">
      <div class="item">1</div>
      <div class="item">2</div>
      <div class="item">3</div>
    </div>
  
    <div class="print-style">
      <div>{@html class_name}</div>
      <!-- Печатаем стили -->
      {#each Object.keys(stl) as item, i}
        <div>{item}: {stl[item]}</div>
      {/each}
      <div>}</div>
    </div>
  </div>
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');
  
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif; /* Используем округлый шрифт */
    }
  
    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      background-color: #ffffff; /* Белый фон */
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
    }
  
    .flex-show {
      display: var(--disp);
      flex-direction: var(--direct);
      justify-content: var(--justcont);
      border: 2px solid #333; /* Темная граница */
      border-radius: 10px;
      width: 318px;
      padding: 10px;
      gap: 10px;
      background-color: #f7f7f7; /* Светло-серый фон для блока */
      transition: all 0.3s ease;
    }
  
    .item {
      background-color: #fff; /* Белый фон для элементов */
      border-radius: 10px; /* Округлые углы */
      padding: 20px;
      text-align: center;
      font-size: 24px;
      font-weight: 600; /* Полужирный шрифт */
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s ease, background 0.3s ease;
    }
  
    .item:hover {
      transform: translateY(-5px);
      background-color: #e0e0e0; /* Светло-серый фон при наведении */
    }
  
    .print-style {
      border: 2px solid #333; /* Темная граница */
      border-radius: 10px;
      width: 200px;
      padding: 20px;
      margin-top: 20px;
      background-color: rgba(255, 255, 255, 0.9);
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }
  </style>
  