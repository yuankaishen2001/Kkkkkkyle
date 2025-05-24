<template>
  <div class="header">
    <div class="header-left">
      <h1>ROLAND</h1>
    </div>
    <nav class="header-right">
      <router-link to="/" class="nav-link">About Me</router-link>
      <router-link to="/publication" class="nav-link">Publication</router-link>
      <router-link to="/education" class="nav-link disabled" title="Coming Soon">Education</router-link>
      <router-link to="/experience" class="nav-link disabled" title="Coming Soon">Experience</router-link>
      <router-link to="/space" class="nav-link disabled" title="Coming Soon">Space</router-link>
    </nav>
  </div>
</template>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 8vh;
  background: linear-gradient(135deg, rgb(0, 93, 233), rgb(58, 154, 236));
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
  z-index: 100;
  box-sizing: border-box;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.header:hover {
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
}

.header-left h1 {
  font-size: 1.5rem;
  margin: 0;
  font-weight: 600;
  letter-spacing: 0.5px;
  transition: transform 0.3s ease;
}

.header-left h1:hover {
  transform: scale(1.05);
}

.header-right {
  display: flex;
  gap: 1.5rem;
  align-items: center;
}

.nav-link {
  color: white;
  text-decoration: none;
  font-weight: 500;
  padding: 0.5rem 0.8rem;
  border-radius: 4px;
  transition: all 0.3s ease;
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 0;
  height: 2px;
  background-color: white;
  transition: all 0.3s ease;
  transform: translateX(-50%);
}

.nav-link:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.nav-link:hover::after {
  width: 80%;
}

.nav-link.router-link-active {
  background-color: rgba(255, 255, 255, 0.15);
}

.nav-link.router-link-active::after {
  width: 80%;
}

.nav-link.disabled {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
  position: relative;
}

.nav-link.disabled::before {
  content: '🚧';
  position: absolute;
  top: -20px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 0.8rem;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.nav-link.disabled:hover::before {
  opacity: 1;
}

@media (max-width: 768px) {
  .header {
    padding: 0 1rem;
  }

  .header-right {
    gap: 0.8rem;
  }

  .nav-link {
    padding: 0.4rem 0.6rem;
    font-size: 0.9rem;
  }
}
</style>