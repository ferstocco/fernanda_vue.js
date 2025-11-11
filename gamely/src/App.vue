<template>
  <div class="app">
    <header class="header">
      <h1 class="logo"><span>GAME</span>LY</h1>
      <nav>Menu ▾</nav>

      <div class="search">
        <input type="text" v-model="busca" placeholder="pesquisar" />
        <button>
          <img :src="LupaRoxa" alt="Buscar" />
        </button>
      </div>

      <div class="cart">
        <img :src="Carrinho" alt="Carrinho" />
        <span class="cart-badge">0</span>
      </div>
    </header>

    <main class="content">
      <aside class="sidebar">
        <p class="breadcrumb">Página Inicial > Loja</p>
        <h2>Categorias</h2>
        <ul>
          <li v-for="cat in categorias" :key="cat.nome">
            <details>
              <summary>{{ cat.nome }} ({{ cat.qtd }})</summary>
            </details>
          </li>
        </ul>
      </aside>

      <section class="store">
        <div class="store-header">
          <h2>Jogos para PC</h2>
          <div class="controls">
            <span>Exibindo 4–20 de 110 resultados</span>
            <select>
              <option>Ordenação padrão v</option>
            </select>
            <select>
              <option>Show 20 v</option>
            </select>
          </div>
        </div>

        <div class="games-grid">
          <div v-for="jogo in jogos" :key="jogo.id" class="game-card">
            <img :src="jogo.imagem" :alt="jogo.titulo" />
            <div class="info">
              <p>Conta Steam</p>
              <h3>{{ jogo.titulo }}</h3>
              <p class="price">
                <span class="novo">R${{ jogo.preco.toFixed(2) }}</span>
                <span class="antigo" v-if="jogo.antigo">R${{ jogo.antigo.toFixed(2) }}</span>
              </p>
              <div class="stars">★★★★★</div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<script>
import LupaRoxa from '@/assets/c4e34a10-d08a-432a-8793-ed15eea0cfab.png'
import Carrinho from '@/assets/c9deaf09-ae72-4b36-a2fa-d00f04f6bf7c.png'


export default {
  data() {
    return {
      busca: '',
      LupaRoxa,
      Carrinho,
      categorias: [
        { nome: 'Anime', qtd: 7 },
        { nome: 'Corrida', qtd: 3 },
        { nome: 'Jogos de tiro', qtd: 9 },
        { nome: 'Jogos de luta', qtd: 9 },
        { nome: 'RPG', qtd: 12 },
        { nome: 'Outros', qtd: 6 },
      ],
     jogos: [
  {
    id: 1,
    titulo: 'Hollow Knight: Silksong',
    preco: 19.9,
    antigo: 78.78,
    imagem: 'https://cdn.akamai.steamstatic.com/steam/apps/1030300/header.jpg',
  },
  {
    id: 2,
    titulo: 'Abiotic Factor',
    preco: 14.9,
    antigo: 19.99,
    imagem: 'https://cdn.akamai.steamstatic.com/steam/apps/427410/header.jpg',
  },
  {
    id: 3,
    titulo: 'Grounded',
    preco: 16.9,
    antigo: 109.9,
    imagem: 'https://cdn.akamai.steamstatic.com/steam/apps/962130/header.jpg',
  },
  {
    id: 4,
    titulo: 'It Takes Two',
    preco: 16.9,
    antigo: 199.9,
    imagem: 'https://cdn.akamai.steamstatic.com/steam/apps/1426210/header.jpg',
  },
],

    }
  },
}
</script>

<style scoped>
.app {
  background: #111;
  color: white;
  font-family: 'Poppins', sans-serif;
  min-height: 100vh;
}

/* ======== CABEÇALHO ======== */
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
  background: #000;
  gap: 1rem;
}

.logo span {
  color: #fff;
  font-weight: 700;
}
.logo {
  color: #b700ff;
  font-weight: 800;
  font-size: 1.8rem;
}

/* ======== BUSCA ======== */
.search {
  display: flex;
  align-items: center;
  background: #1c1c1c;
  border-radius: 999px;
  padding: 0.3rem 0.7rem;
  width: 450px;
  max-width: 100%;
}
.search input {
  flex: 1;
  background: transparent;
  border: none;
  color: #fff;
  outline: none;
  font-size: 1rem;
  padding: 0.4rem 0.6rem;
}
.search button {
  background: transparent;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  width: 45px;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  transition: transform 0.3s ease, filter 0.3s ease;
}
.search button img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 12px;
  transition: filter 0.3s ease, box-shadow 0.3s ease;
}
.search button:hover {
  transform: scale(1.1);
}
.search button:hover img {
  filter: brightness(1.3);
  box-shadow: 0 0 12px #b700ff, 0 0 25px #b700ff66;
}

/* ======== CARRINHO ======== */
.cart {
  position: relative;
  width: 45px;
  height: 45px;
  cursor: pointer;
  transition: transform 0.3s ease;
}
.cart img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
.cart:hover {
  transform: scale(1.1);
}
.cart-badge {
  position: absolute;
  top: -6px;
  right: -4px;
  background: #b700ff;
  color: white;
  font-size: 0.8rem;
  font-weight: bold;
  border-radius: 50%;
  padding: 0.2rem 0.5rem;
}


.content {
  display: flex;
  padding: 2rem;
}


.sidebar {
  width: 250px;
  padding-right: 2rem;
  border-right: 1px solid #333;
}
.sidebar h2 {
  margin-top: 1rem;
}
.sidebar ul {
  list-style: none;
  padding: 0;
}
.sidebar summary {
  cursor: pointer;
  font-weight: bold;
  margin: 0.5rem 0;
}


.store {
  flex: 1;
  padding-left: 2rem;
}
.store-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.controls {
  display: flex;
  gap: 1rem;
  align-items: center;
  position: relative;
}


.controls select {
  background-color: #111;       
  color: #fff;                  
  border: 1px solid #333;       
  border-radius: 12px;          
  padding: 0.4rem 0.6rem;      
  font-size: 0.9rem;
  cursor: pointer;
  outline: none;
  appearance: none;             
  position: relative;
}

.controls select:hover {
  border-color: #b700ff;        
}

.controls select:focus {
  border-color: #b700ff;
  box-shadow: 0 0 6px #b700ff66;
}


.controls select::-ms-expand {
  display: none; 
}

.games-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}
.game-card {
  background: #222;
  border-radius: 8px;
  overflow: hidden;
  text-align: center;
  transition: transform 0.2s;
}
.game-card:hover {
  transform: scale(1.03);
}
.game-card img {
  width: 100%;
  height: 260px;
  object-fit: cover;
}
.info {
  padding: 0.8rem;
}
.price {
  margin: 0.5rem 0;
}
.novo {
  color: #fff;
  font-weight: bold;
  margin-right: 0.5rem;
}
.antigo {
  color: gray;
  text-decoration: line-through;
}
.stars {
  color: #b700ff;
}
</style>
