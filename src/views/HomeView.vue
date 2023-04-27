<script setup>
import { ref } from 'vue'
const names = ref(['Selina Damo', 'Cavin Johnstone', 'Lena Oxton'])
const nameInput = ref('')
const addPerson = () => {
  names.value.unshift(nameInput.value)
  nameInput.value = ''
}

const removePerson = (name) => {
  names.value = names.value.filter((n) => n !== name)
}
</script>

<template>
  <main>
    <!-- <div class="container">
      <Transition name="fade">
        <h1 v-if="showGreet">Hello</h1>
        <h1 v-else>Goodbuy</h1>
      </Transition>
    </div>
    <button @click= "showGreet = !showGreet">Toggle</button> -->
    <div class="container">
      <input
        type="text"
        placeholder="Please write your guest name"
        v-model="nameInput"
        @keypress.enter="addPerson"
      />
      <TransitionGroup name="persons">
        <li v-for="name in names" @click="removePerson(name)" :key="name" tag="ul">{{ name }}</li>
      </TransitionGroup>
    </div>
  </main>
</template>

<style lang="scss" scoped>
.container {
  max-width: 300px;
  margin: auto;
  transform: scale(1.7);

  input {
    width: 100%;
    border-radius: 5px;
    border: 1px solid rgba(128, 128, 128, 0.13);
    padding: 10px;
    margin-bottom: 20px;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.12);
  }

  // ul {
  //   display: inline;
  //   list-style: none;
  //   margin: 0;
  //   padding: 0;

  li {
    list-style: none;
    width: 300px;
    border-radius: 5px;
    padding: 5px 10px;
    margin-top: 10px;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.12);
    text-align: center;
    cursor: pointer;
  }
}

// TRANSITION
.persons-enter-from {
  opacity: 0;
  transform: scale(0.5);
}
.persons-enter-to {
  opacity: 1;
  transform: scale(1); //default state but leave it here
}
.persons-enter-active {
  transition: all 0.5s ease;
}
.persons-leave-from {
  opacity: 1;
  transform: scale(1);
}
.persons-leave-to {
  opacity: 0;
  transform: scale(0); //default state but leave it here
}
.persons-leave-active {
  transition: all 0.5s ease;
  position: absolute;
}

.persons-move {
  transition: all 0.5s ease;
}

// .container {
//   position: relative;

//   h1 {
//     position: absolute;
//     margin: 5px;
//   }
// }

// button {
//   margin-top: 50px;
// }
// /* animate color from */
// .fade-enter-from {
//   opacity: 0;
// }

// .fade-enter-to {
//   opacity: 1;
// }

// .fade-enter-active {
//   transition: all 0.5s ease;
// }

// .fade-leave-from {
//   opacity: 1;
// }

// .fade-leave-to {
//   opacity: 0;
// }

// .fade-leave-active {
//   transition: all 0.5s ease;
// }
</style>
