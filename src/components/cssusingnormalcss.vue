<style scoped>
.container {
  display: grid;  /* base */
  grid-template-columns: 1fr 1fr;  /* base */
  grid-template-rows: 2fr 3fr;  /* base */
  gap: 1.5rem;  /* base */
  max-width: 900px; /* base */
  margin: 3rem auto; /* base */
  /* padding: 1.5rem; */
  /* font-family: Arial, sans-serif;  */
}

/* Top section */
.big {
  grid-column: 1 / 3; /* base */
  /* background: #1e293b;
  color: white;
  padding: 2rem;
  border-radius: 1rem; */
  text-align: center; /* base */
}

.big h1 {
  /* font-size: 1.5rem;
  margin-bottom: 1rem; */
}

form {
  display: flex; /* base */
  /* gap: 0.75rem; */
  justify-content: center; /* base */
}

input {
  flex: 1; /* base */
  /* max-width: 25rem;
  padding: 0.8rem;
  border: none;
  border-radius: 0.5rem;
  font-size: 1rem;
  outline: none; */
}

button {
  /* padding: 0.7rem 1rem;
  border: none;
  border-radius: 0.5rem;
  background: #3b82f6;
  color: white;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.2s; */
}

button:hover {
  /* background: #2563eb; */
}

/* To-do and Done sections */
.box {
  /* background: #f8fafc;
  padding: 1.5rem;
  border-radius: 1rem;
  border: 1px solid #e2e8f0;
  min-width: 0; */
}

.box p {
  /* font-size: 1.3rem;
  font-weight: bold;
  color: #1e293b;
  margin: 0; */
}

ul {
  /* list-style: none;
  padding: 0;
  margin: 0; */
}

li {
  display: flex; /* base */
  justify-content: space-between; /* base */
  align-items: center; /* base */
  /* gap: 0.75rem;
  padding: 0.8rem;
  margin-bottom: 0.7rem;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 0.6rem;
  color: #334155; */
  overflow-wrap: anywhere; /* base */
}

li button {
  flex-shrink: 0; /* base */
  /* font-size: 0.8rem; */
}

.box:last-child li button {
  /* background: #ef4444; */
}

.box:last-child li button:hover {
  /* background: #dc2626; */
}

/* Responsive design */
@media (max-width: 600px) {
  .container {
    grid-template-columns: 1fr;
    grid-template-rows: auto;
    margin: 1rem auto;
    padding: 1rem;
  }

  .big {
    grid-column: 1;
  }

  form {
    flex-direction: column;
  }

  input {
    max-width: none;
  }

  li {
    flex-wrap: wrap;
  }
}
</style>