# Vue3 + Vite + Hardhat + WindiCSS Ethereum dApp skeleton

This is a very, very basic setup to get started with building dApps with Vue3, Vite, Hardhat and WindiCSS.

The basic setup is taken from [Nader Dabit]()s awesome post [The Complete Guide to Full Stack Ethereum Development](https://dev.to/dabit3/the-complete-guide-to-full-stack-ethereum-development-3j13). I just used Vite + Vue3 instead of React because a) I like Vue better than React and b) Vite is fast.

## Installation

1. Use the basic setup described in Naders blog post You'll need [MetaMask](https://metamask.io/) for at least the local testing.
1. Clone this repo via `git clone git@github.com:HerrBertling/simple-vite-eth.git`
1. Run `yarn` to install all dependencies
1. Follow the steps outlined in Naders blog post, but swap the React parts and use Vue instead.
1. The fun stuff happens in the [`App.vue` file](https://github.com/HerrBertling/simple-vite-eth/blob/main/src/App.vue), but I've just adjusted Naders code to Vue (and threw in a `fetchGreeting` on mounting the app). Also, the dev server starts with `yarn dev`, not with `npm start` as in the blog post.