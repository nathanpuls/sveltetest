<!-- src/components/Nav.svelte -->

<script>
    // Import necessary Svelte modules
    import { onMount } from 'svelte';
  </script>
  
  <style>
    /* Add your styling here */
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px;
      background-color: #333;
      color: rgb(255, 255, 255);
    }
  
    .brand {
      font-size: 1.5em;
      font-weight: bold;
      color: #ffffff;
    }
  
    .nav-link {
      color: #fff;
      text-decoration: none;
      margin-right: 10px;
    }
  </style>
  
  <!-- HTML template for the Nav component -->
  <nav>
    <!-- Brand/Logo on the left -->
    <div class="brand"> Brand</div>
  
    <!-- Navigation Link on the right -->
    <a href="/" class="nav-link">Home</a>
  </nav>
  