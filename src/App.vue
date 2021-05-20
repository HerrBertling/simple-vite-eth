<template>
<div class="prose lg:prose-xl mx-auto mt-16"> 
  <HelloWorld :msg="greeting" />
  <div class="flex gap-8">
    <BaseButton @click="fetchGreeting">Fetch Greeting</BaseButton>
    <BaseButton @click="setGreeting">Set Greeting</BaseButton>
    <BaseInput v-model="greeting" placeholder="Set greeting" />
  </div>
</div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { ethers } from 'ethers'
import Greeter from './artifacts/contracts/Greeter.sol/Greeter.json'
import HelloWorld from './components/HelloWorld.vue'
import BaseButton from './components/BaseButton.vue'
import BaseInput from './components/BaseInput.vue'

const greeterAddress = "thisShouldBeYourGreeterAdress"

const greeting = ref('');

const requestAccount = async () => {
    await window.ethereum.request({ method: 'eth_requestAccounts' });
  }

const fetchGreeting = async () => {
    if (typeof window.ethereum !== 'undefined') {
      const provider = new ethers.providers.Web3Provider(window.ethereum)
      const contract = new ethers.Contract(greeterAddress, Greeter.abi, provider)
      try {
        const data = await contract.greet()
        greeting.value = data
      } catch (err) {
        console.log("Error: ", err)
      }
    }    
  }

  // call the smart contract, send an update
const setGreeting = async () => {
    if (!greeting) return
    if (typeof window.ethereum !== 'undefined') {
      await requestAccount()
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      const signer = provider.getSigner()
      const contract = new ethers.Contract(greeterAddress, Greeter.abi, signer)
      const transaction = await contract.setGreeting(greeting.value)
      await transaction.wait()
      fetchGreeting()
    }
  }

  onMounted(() => {
    fetchGreeting()
  })
</script>