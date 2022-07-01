<script>
  import Kenshi from "src/icons/Kenshi.svelte";
  import ChevronRight from "src/icons/ChevronRight.svelte";

  import Card from "./Card.svelte";

  import { fly } from "svelte/transition";

  import Shuffle from "src/icons/Shuffle.svelte";
  import LiquidUp from "src/icons/LiquidUp.svelte";

  import DB from "src/icons/DB.svelte";
  import D20 from "src/icons/D20.svelte";
  import CloudSensor from "src/icons/CloudSensor.svelte";

  import BinaryLock from "src/icons/BinaryLock.svelte";
  import Shield from "src/icons/Shield.svelte";
  import Code from "src/icons/Code.svelte";

  import NPM from "src/icons/NPM.svelte";
  import Github from "src/icons/Github.svelte";
  import Medium from "src/icons/Medium.svelte";
  import Telegram from "src/icons/Telegram.svelte";
  import Book from "src/icons/Book.svelte";
  import Discord from "src/icons/Discord.svelte";

  import Node from "src/icons/Node.svelte";
  import Python from "src/icons/Python.svelte";
  import Go from "src/icons/Go.svelte";

  import HexagonCheck from "src/icons/HexagonCheck.svelte";
  import Dashboard from "src/icons/Dashboard.svelte";

  import Coin from "src/icons/Coin.svelte";
  import ListCheck from "src/icons/ListCheck.svelte";
  import Scale from "src/icons/Scale.svelte";
  import Swap from "src/icons/Swap.svelte";
  import Faucet from "src/icons/Faucet.svelte";
  import Tools from "src/icons/Tools.svelte";
  import CreditCard from "src/icons/CreditCard.svelte";
  import Pancake from "src/icons/Pancake.svelte";
  import ChartLine from "src/icons/ChartLine.svelte";
  import SquareQuestion from "src/icons/SquareQuestion.svelte";
  import BarcodeRead from "src/icons/BarcodeRead.svelte";

  import Twitter from "../icons/Twitter.svelte";
  import Reddit from "../icons/Reddit.svelte";
  import LinkedIn from "../icons/LinkedIn.svelte";

  import Bars from "src/icons/Bars.svelte";
  import ChevronLeft from "src/icons/ChevronLeft.svelte";
  import Xmark from "src/icons/Xmark.svelte";

  import Products from "src/icons/Products.svelte";
  import Community from "src/icons/Community.svelte";
  import Briefcase from "src/icons/Briefcase.svelte";

  import Newspaper from "src/icons/Newspaper.svelte";
  import UserGear from "src/icons/UserGear.svelte";
  import UserHeadset from "src/icons/UserHeadset.svelte";
  import UserSecret from "src/icons/UserSecret.svelte";
  import UserTie from "src/icons/UserTie.svelte";
  import Palette from "src/icons/Palette.svelte";
  import Team from "src/icons/Team.svelte";

  import Link from "./Link.svelte";

  import ConnectButton from "./ConnectButton.svelte";

  let menus = {};

  const allClosed = () =>
    Object.fromEntries(Object.entries(menus).map(([k]) => [k, false]));

  const openMenu = (menu) => {
    menus = { ...allClosed(), [menu]: true };
  };

  const closeMenu = (menu) => {
    menus = { ...allClosed(), [menu]: false };
  };

  let currentOpenMenu = null;
  $: currentOpenMenu = Object.entries(menus)
    .find(([_, state]) => state)
    ?.shift?.();

  let lastOpenMenu;
  $: lastOpenMenu = currentOpenMenu || lastOpenMenu;

  let anyMenuOpen;
  $: if (anyMenuOpen != !!currentOpenMenu) {
    anyMenuOpen = !!currentOpenMenu;
  }

  let closeTimeout;

  const menuAction = (el, name) => {
    const onEnter = () => {
      clearTimeout(closeTimeout);
      openMenu(name || lastOpenMenu);
    };
    const onLeave = () => {
      if (isMobile) return;
      closeTimeout = setTimeout(() => closeMenu(name || lastOpenMenu), 250);
    };
    let eventEnterType = (isMobile) ? "click" : "mouseenter"
    let eventLeaveType = (isMobile) ? "click" : "mouseleave"
    el.addEventListener(eventEnterType, onEnter);
    el.addEventListener(eventLeaveType, onLeave);
    return () => {
      el.removeEventListener(eventEnterType, onEnter);
      el.removeEventListener(eventLeaveType, onLeave);
    };
  };

  const dropActionMobile = (el, name) => {
    const onClick = () => {
      if (!menus.mobile && anyMenuOpen) {
        menus = { ...allClosed(), mobile: true };
      } else if (menus.mobile) {
        menus = { ...allClosed() };
      } else {
        openMenu(name);
      }
      return false;
    };
    el.addEventListener("click", onClick);
    return () => {
      el.removeEventListener("click", onClick);
    };
  };

  let innerHeight;

  const submenuSlide = (node) => {
    innerHeight = getComputedStyle(node).height;
    return {
      delay: 0,
      duration: 200,
      css: (t) => `
        transform: translateX(${600 - t * 600}px);
        opacity: ${t};
      `,
    };
  };

  let y;
  let scrolled = false;
  $: scrolled = y > 0;

  let innerWidth = 0;
  $: isMobile = innerWidth < 1050;
</script>

<svelte:window bind:scrollY={y} bind:innerWidth />

<div
  class="navbar"
  class:mobile={isMobile}
  class:open={anyMenuOpen}
  class:shadow={scrolled}
>
  {#if isMobile}
    <div class="menu">
      <span>
        <button class="flat bars" use:dropActionMobile={"mobile"}>
          {#if menus.mobile}
            <Xmark />
          {:else if anyMenuOpen}
            <ChevronLeft />
          {:else}
            <Bars />
          {/if}
        </button>
      </span>
    </div>
  {/if}
  <span class="logo">
    <a href="/">
      <Kenshi />
    </a>
  </span>
  <div class="menu">
    {#if !isMobile}
      <span class:active={menus["products"]}>
        <button class="flat" use:menuAction={"products"}> Products </button>
      </span>
      <span class:active={menus["dev"]}>
        <button class="flat" use:menuAction={"dev"}> Developers </button>
      </span>
      <span class:active={menus["token"]}>
        <button class="flat" use:menuAction={"token"}> Token </button>
      </span>
      <span class:active={menus["community"]}>
        <button class="flat" use:menuAction={"community"}> Community </button>
      </span>
      <span class:active={menus["company"]}>
        <button class="flat" use:menuAction={"company"}> Company </button>
      </span>
    {/if}
  </div>
  <div class="spacer" />
  <ConnectButton {isMobile} />
  <a href="/dashboard" class="button build">
    <span>
      {#if isMobile}
        Start
      {:else}
        Build with Kenshi
      {/if}
      <ChevronRight /></span
    >
  </a>
</div>

{#if anyMenuOpen}
  <div
    class="submenu"
    class:mobile={isMobile}
    use:menuAction
    transition:fly={{ y: 80, duration: 200 }}
  >
    <Card>
      <div class="submenu-inner" style="--inner-height: {innerHeight}">
        {#if menus.mobile}
          <div class:active={menus["products"]}>
            <button class="flat" use:menuAction={"products"}>
              <Products /> Products <ChevronRight />
            </button>
          </div>
          <div class:active={menus["dev"]}>
            <button class="flat" use:menuAction={"dev"}>
              <Code /> Developers <ChevronRight />
            </button>
          </div>
          <div class:active={menus["token"]}>
            <button class="flat" use:menuAction={"token"}>
              <Coin /> Token <ChevronRight />
            </button>
          </div>
          <div class:active={menus["community"]}>
            <button class="flat" use:menuAction={"community"}>
              <Community /> Community <ChevronRight />
            </button>
          </div>
          <div class:active={menus["company"]}>
            <button class="flat" use:menuAction={"company"}>
              <Briefcase /> Company <ChevronRight />
            </button>
          </div>
        {:else if menus.products}
          <div in:submenuSlide>
            <div class="products">
              <div class="product">
                <h3>Deep Index</h3>
                <div>
                  <Link
                    href="https://docs.kenshi.io/services/deep-index/sync/index.html"
                  >
                    <DB />Indexing
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://docs.kenshi.io/services/deep-index/webhook/index.html"
                  >
                    <CloudSensor />Reverse API
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://docs.kenshi.io/services/deep-index/graphql/index.html"
                  >
                    <D20 />GraphQL
                  </Link>
                </div>
              </div>
              <div class="product">
                <h3>Oracles</h3>
                <div>
                  <Link href="https://docs.kenshi.io/services/vrf/index.html">
                    <Shuffle />VRF
                  </Link>
                </div>
                <div>
                  <Link href="https://docs.kenshi.io/services/lbp.html">
                    <LiquidUp />Liquidity Bootstrapping
                  </Link>
                </div>
              </div>
              <div class="product">
                <h3>Services</h3>
                <div>
                  <Link href="/dashboard">
                    <Dashboard /> Dashboard
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://docs.kenshi.io/services/audits/index.html"
                  >
                    <Shield />Security Audits
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://docs.kenshi.io/services/development/index.html"
                  >
                    <Code />Blockchain Development
                  </Link>
                </div>
              </div>
              <div class="product">
                <h3>Other</h3>
                <div>
                  <Link href="/lockers">
                    <BinaryLock /> Liquidity Lockers
                  </Link>
                </div>
              </div>
            </div>
          </div>
        {:else if menus.dev}
          <div in:submenuSlide>
            <div class="devs">
              <div class="dev">
                <h3>Resources</h3>
                <div>
                  <Link href="/dashboard">
                    <Dashboard /> Dashboard
                  </Link>
                </div>
                <div>
                  <Link href="https://docs.kenshi.io">
                    <Book /> Documentation
                  </Link>
                </div>
                <div>
                  <Link href="https://github.com/kenshi-token" target="_blank">
                    <Github /> Github
                  </Link>
                </div>
                <div>
                  <Link href="https://blog.kenshi.io"><Medium /> Medium</Link>
                </div>
                <div>
                  <Link href="https://t.me/kenshi_developers" target="_blank">
                    <Telegram /> Telegram
                  </Link>
                </div>
                <div>
                  <Link href="https://discord.gg/y4f5Rh5Apq" target="_blank">
                    <Discord /> Discord
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://www.npmjs.com/org/kenshi.io"
                    target="_blank"
                  >
                    <NPM /> NPM
                  </Link>
                </div>
              </div>
              <div class="dev">
                <h3>Deep Index Examples</h3>
                <h4>GraphQL</h4>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/graphql-example-node-fetch"
                    target="_blank"
                  >
                    <Node /> Node.js (fetch)
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/graphql-example-node-axios"
                    target="_blank"
                  >
                    <Node /> Node.js (axios)
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/graphql-example-python"
                    target="_blank"
                  >
                    <Python /> Python
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/graphql-example-go"
                    target="_blank"
                  >
                    <Go /> Go
                  </Link>
                </div>
              </div>
              <div class="dev">
                {#if !isMobile}
                  <h3>‌</h3>
                {/if}
                <h4>Reverse API</h4>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/reverse-api-example-node"
                    target="_blank"
                  >
                    <Node /> Node.js
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/reverse-api-example-python"
                    target="_blank"
                  >
                    <Python /> Python
                  </Link>
                </div>
              </div>
              <div class="dev">
                <h3>Randomness</h3>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/d20"
                    target="_blank"
                  >
                    <D20 /> D20 Smart Contract
                  </Link>
                </div>
              </div>
              <div class="dev">
                <h3>Other</h3>
                <div>
                  <Link href="/status">
                    <HexagonCheck /> Service Status
                  </Link>
                </div>
              </div>
            </div>
          </div>
        {:else if menus.token}
          <div in:submenuSlide>
            <div class="tokens">
              <div class="token">
                <h3>About</h3>
                <div>
                  <Link href="https://docs.kenshi.io/token/tokenomics.html">
                    <Coin /> Tokenomics
                  </Link>
                </div>
                <div>
                  <Link href="https://docs.kenshi.io/token/features/index.html">
                    <ListCheck /> Features
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://docs.kenshi.io/token/features/variable-tax.html"
                  >
                    <Scale /> Tax
                  </Link>
                </div>
              </div>
              <div class="token">
                <h3>Trade</h3>
                <div>
                  <Link href="/swap">
                    <CreditCard /> Buy
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://pancakeswap.finance/swap?outputCurrency=0x42f9c5a27a2647a64f7D3d58d8f896C60a727b0f"
                    target="_blank"
                  >
                    <Pancake /> Buy on PancakeSwap
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://charts.bogged.finance/?c=bsc&t=0x42f9c5a27a2647a64f7D3d58d8f896C60a727b0f"
                    target="_blank"
                  >
                    <ChartLine /> Charts
                  </Link>
                </div>
              </div>
              <div class="token">
                <h3>Tools</h3>
                <div>
                  <Link href="/tools">
                    <Tools /> Tools
                  </Link>
                </div>
                <div>
                  <Link href="/pegswap">
                    <Swap /> PegSwap
                  </Link>
                </div>
                <div>
                  <Link href="/faucet">
                    <Faucet /> Faucet
                  </Link>
                </div>
              </div>
              <div class="token">
                <h3>Resources</h3>
                <div>
                  <Link
                    href="https://blog.kenshi.io/how-to-buy-the-kenshi-token-30ab03372fd4"
                  >
                    <SquareQuestion /> How to buy
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://bscscan.com/token/0x42f9c5a27a2647a64f7D3d58d8f896C60a727b0f"
                    target="_blank"
                  >
                    <BarcodeRead /> BscScan
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://github.com/kenshi-token/contracts"
                    target="_blank"
                  >
                    <Code /> Source code
                  </Link>
                </div>
              </div>
            </div>
          </div>
        {:else if menus.community}
          <div in:submenuSlide>
            <div class="communities">
              <div class="community">
                <h3>Chat</h3>
                <div>
                  <Link href="https://t.me/kenshi_token" target="_blank">
                    <Telegram /> Community Chat
                  </Link>
                </div>
                <div>
                  <Link href="https://t.me/kenshi_developers" target="_blank">
                    <Telegram /> Dev Chat
                  </Link>
                </div>
                <div>
                  <Link href="https://discord.gg/y4f5Rh5Apq" target="_blank">
                    <Discord /> Discord
                  </Link>
                </div>
              </div>
              <div class="community">
                <h3>Social Media</h3>
                <div>
                  <Link href="https://twitter.com/kenshi_token" target="_blank">
                    <Twitter /> Twitter
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://www.reddit.com/r/kenshi_token/"
                    target="_blank"
                  >
                    <Reddit /> Reddit
                  </Link>
                </div>
                <div>
                  <Link
                    href="https://www.linkedin.com/company/kenshiio/"
                    target="_blank"
                  >
                    <LinkedIn /> LinkedIn
                  </Link>
                </div>
              </div>
              <div class="community">
                <h3>Other</h3>
                <div>
                  <Link href="https://blog.kenshi.io"><Medium /> Medium</Link>
                </div>
                <div>
                  <Link href="https://github.com/kenshi-token" target="_blank">
                    <Github /> Github
                  </Link>
                </div>
              </div>
            </div>
          </div>
        {:else if menus.company}
          <div in:submenuSlide>
            <div class="communities">
              <div class="community">
                <h3>About</h3>
                <div>
                  <Link href="https://docs.kenshi.io/kenshi.html">
                    <Briefcase /> Kenshi
                  </Link>
                </div>
                <div>
                  <Link href="https://docs.kenshi.io/team.html">
                    <Team /> Team
                  </Link>
                </div>
              </div>
              <div class="community">
                <h3>Resources</h3>
                <div>
                  <Link
                    href="https://www.linkedin.com/company/kenshiio/"
                    target="_blank"
                  >
                    <LinkedIn /> LinkedIn
                  </Link>
                </div>
                <div>
                  <Link href="https://blog.kenshi.io">
                    <Medium /> Blog
                  </Link>
                </div>
              </div>
              <div class="community">
                <h3>Press</h3>
                <div>
                  <Link href="https://docs.kenshi.io/media.html">
                    <Palette />
                    Press Kit
                  </Link>
                </div>
                <div>
                  <Link href="mailto:press@kenshi.io">
                    <Newspaper /> Press Inquiries
                  </Link>
                </div>
              </div>
              <div class="community">
                <h3>Contacts</h3>
                <div>
                  <Link href="mailto:experts@kenshi.io">
                    <UserGear />
                    Talk to an expert
                  </Link>
                </div>
                <div>
                  <Link href="mailto:security@kenshi.io">
                    <UserSecret /> Security
                  </Link>
                </div>
                <div>
                  <Link href="mailto:support@kenshi.io">
                    <UserHeadset /> Support
                  </Link>
                </div>
                <div>
                  <Link href="mailto:inquiries@kenshi.io">
                    <UserTie /> Business Inquiries
                  </Link>
                </div>
              </div>
            </div>
          </div>
        {/if}
      </div>
    </Card>
  </div>
{/if}

{#if anyMenuOpen && isMobile}
  <style global>
    body {
      overflow: hidden;
    }
  </style>
{/if}

<style>
  button {
    cursor: pointer;
  }
  .navbar {
    display: flex;
    padding: 0em 4em;
    align-items: center;
    position: sticky;
    top: 0;
    background: var(--secondary-lighten-4);
    z-index: 1000;
  }
  @media only screen and (max-width: 1280px) {
    .navbar {
      padding: 0em 4em;
    }
  }
  @media only screen and (max-width: 640px) {
    .navbar {
      padding: 0em 1em;
    }
  }
  .navbar.shadow {
    box-shadow: 1em 1em 2em 0.25em rgb(0 0 0 / 10%);
    background: #fafafa;
  }
  .navbar.shadow + .submenu button,
  .navbar.shadow button {
    background: #fafafa;
  }
  .logo :global(svg) {
    fill: var(--primary-color);
    height: 32px;
  }
  .logo {
    display: flex;
    gap: 1em;
    align-items: center;
  }
  .spacer {
    flex: 1;
  }
  .menu {
    display: flex;
    align-items: center;
    padding: 0 2em;
  }
  @media only screen and (max-width: 1280px) {
    .menu {
      padding: 0em 0.5em;
    }
  }
  .submenu {
    position: fixed;
    z-index: 1000;
    width: 100%;
    padding: 0em 4em;
    box-sizing: border-box;
  }
  .submenu.mobile {
    width: 100%;
    height: 100%;
    padding: 0;
  }
  .submenu-inner {
    background: #fafafa;
    position: relative;
    height: var(--inner-height);
    transition: cubic-bezier(0.165, 0.84, 0.44, 1) 0.2s all;
  }
  @media screen and (max-width: 1050px) {
    .submenu :global(.card) {
      overflow-y: scroll;
      max-height: calc(100vh - 64px);
      padding-bottom: 2em !important;
      box-sizing: border-box;
    }
  }
  .build :global(svg) {
    fill: var(--primary-color);
  }
  .menu span {
    position: relative;
    padding-bottom: 1em;
    padding-top: 1em;
  }
  .menu .active button {
    background: rgba(0, 0, 0, 0.05);
  }
  button {
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
    padding: 0.5em 1em;
    font-size: 1em;
    background: var(--secondary-lighten-4);
    border-radius: 0.5em;
    display: flex;
    align-items: center;
    gap: 0.75em;
  }
  button.flat {
    color: #000;
    border: none;
    font-size: 1em;
    background: transparent;
  }
  button :global(svg) {
    height: 0.8em;
  }
  .button:not(.flat) {
    position: relative;
  }
  .button:not(.flat):hover {
    color: #fff;
  }
  .button > span {
    z-index: 1;
  }
  .button:not(.flat)::after {
    content: "";
    position: absolute;
    right: 0;
    top: -1px;
    bottom: -1px;
    width: 0;
    background: var(--primary-color);
    transition: width cubic-bezier(0.165, 0.84, 0.44, 1) 0.1s;
    z-index: 0;
    border-radius: 0.5em;
  }
  .button:not(.flat):hover::after {
    width: 100%;
  }
  .button {
    transition: transform cubic-bezier(0.175, 0.885, 0.32, 1.275) 0.2s;
  }
  .button:active {
    transform: scale(0.98);
  }
  .bars {
    width: 2.3em;
  }
  .bars :global(svg) {
    height: 1.5em;
  }
  .bars {
    padding: 0.25em;
    padding-right: 1em;
    padding-left: 0;
  }
  a.button {
    color: var(--primary-color);
    border: 1px solid var(--primary-color);
    padding: 0.5em 1em;
    background: transparent;
    font-size: 1em;
    border-radius: 0.5em;
    display: flex;
    align-items: center;
    gap: 0.75em;
  }
  .button > span {
    display: flex;
    align-items: center;
    gap: 0.5em;
  }
  a.button :global(svg) {
    height: 0.8em;
    fill: currentColor;
  }
  h3,
  h4 {
    margin-top: 0;
  }
  h4 {
    margin-bottom: 0.5em;
  }
  .products {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(230px, 1fr));
    gap: 1em;
  }
  .product {
    display: flex;
    flex-direction: column;
    gap: 0.5em;
  }
  .product > div {
    display: flex;
    gap: 1em;
    align-items: center;
  }
  .product > div :global(svg) {
    width: 1em;
  }
  .devs {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 2em;
  }
  .dev {
    display: flex;
    flex-direction: column;
    gap: 0.5em;
  }
  .dev > div:not(.duo) {
    display: flex;
    gap: 1em;
    align-items: center;
  }
  .dev > div :global(svg) {
    width: 1em;
  }
  .tokens {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 2em;
  }
  .token {
    display: flex;
    flex-direction: column;
    gap: 0.5em;
  }
  .token > div {
    display: flex;
    gap: 1em;
    align-items: center;
  }
  .token > div :global(svg) {
    width: 1em;
  }
  .communities {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 2em;
  }
  .community {
    display: flex;
    flex-direction: column;
    gap: 0.5em;
  }
  .community > div {
    display: flex;
    gap: 1em;
    align-items: center;
  }
  .community > div :global(svg) {
    width: 1em;
  }
  .mobile h3 {
    margin-top: 1em;
  }
  .navbar button {
    font-weight: bold;
  }
  .button.build {
    margin-left: 0.5em;
  }
</style>
