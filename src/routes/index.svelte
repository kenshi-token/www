<script>
  import Navbar from "src/components/Navbar.svelte";
  import Footer from "src/components/Footer.svelte";
  import Button from "src/components/Button.svelte";
  import CardButton from "src/components/CardButton.svelte";
  import Article from "src/components/Article.svelte";
  import InfoCard from "src/components/InfoCard.svelte";
  import Product from "src/components/Product.svelte";
  import Usage from "src/components/Usage.svelte";

  import VR from "src/icons/VR.svelte";
  import Dice from "src/icons/Dice.svelte";
  import Gamepad from "src/icons/Gamepad.svelte";
  import Slot from "src/icons/Slot.svelte";
  import Shuffle from "src/icons/Shuffle.svelte";

  import DB from "src/icons/DB.svelte";
  import D20 from "src/icons/D20.svelte";
  import Magnify from "src/icons/Magnify.svelte";
  import CloudSensor from "src/icons/CloudSensor.svelte";

  import ChevronRight from "src/icons/ChevronRight.svelte";
  import External from "src/icons/External.svelte";
  import Arrow from "src/icons/Arrow.svelte";

  import BinaryLock from "src/icons/BinaryLock.svelte";
  import LiquidUp from "src/icons/LiquidUp.svelte";
  import Shield from "src/icons/Shield.svelte";
  import Code from "src/icons/Code.svelte";

  import LayerPlus from "src/icons/LayerPlus.svelte";
  import Infinity from "src/icons/Infinity.svelte";
  import Bolt from "src/icons/Bolt.svelte";
  import CheckDouble from "src/icons/CheckDouble.svelte";
  import BellOn from "src/icons/BellOn.svelte";
  import ChartNetwork from "src/icons/ChartNetwork.svelte";
  import Link from "src/icons/Link.svelte";

  import Gist from "src/components/Gist.svelte";
  import Alert from "src/components/Alert.svelte";
</script>

<Navbar />

<!-- Hero -->

<div class="hero">
  <div class="content">
    <img src="/images/kenshi.logo.long.png" alt="Kenshi" class="logo" />
    <div class="motto">Cutting-edge tech for your blockchain projects</div>
    <div class="buttons">
      <Button href="/dashboard">
        Dashboard <ChevronRight />
      </Button>
      <Button href="http://docs.kenshi.io/" target="_blank">
        Read the docs <ChevronRight />
      </Button>
      <Button
        solid
        href="https://charts.bogged.finance/?c=bsc&t=0x42f9c5a27a2647a64f7D3d58d8f896C60a727b0f"
        target="_blank"
      >
        View charts <External />
      </Button>
    </div>
  </div>
  <div class="graphics">
    <img src="/images/kenshi.png" alt="Kenshi Samurai" />
  </div>
</div>

<div class="products">
  <div class="mask">
    <img src="/images/mask.png" alt="Mask" />
  </div>
  <div class="start">
    <h2>Start using Kenshi <br /> for your awesome products.</h2>
    <div class="content">
      From development to deployment and further, Kenshi is on your side.
    </div>
  </div>
  <div class="products-list">
    <Product
      title="VRF Oracle"
      description="Implement dynamic NFTs, games, lotteries and more with Kenshi VRF oracles."
      buttons={[
        {
          href: "https://docs.kenshi.io/services/vrf/index.html",
          external: true,
          label: "Docs",
        },
        {
          href: "https://blog.kenshi.io/introducing-the-kenshi-vrf-oracle-be1cbc4779c9",
          external: false,
          label: "Learn more",
        },
      ]}
    >
      <Shuffle />
      <VR />
      <Dice />
      <Gamepad />
      <Slot />
    </Product>

    <Product
      title="Deep Index"
      description="Sync, search, query, and consume blockchain data that matters."
      buttons={[
        {
          href: "https://docs.kenshi.io/services/deep-index/index.html",
          external: true,
          label: "Docs",
        },
        {
          href: "https://blog.kenshi.io/introducing-the-kenshi-deep-blockchain-indexing-services-7fc4b159a946",
          external: false,
          label: "Learn more",
        },
      ]}
    >
      <D20 />
      <DB />
      <Magnify />
      <CloudSensor />
    </Product>
  </div>
</div>

<div class="discover">
  <h2>Discover all of Kenshi.</h2>
  <div class="products-list">
    <a href="/lockers" class="product">
      <BinaryLock />
      <h3>Liquidity Lockers</h3>
      <Arrow />
    </a>
    <a href="https://docs.kenshi.io/services/lbp.html" class="product">
      <LiquidUp />
      <h3>Liquidity Bootstrapping</h3>
      <Arrow />
    </a>
    <a href="https://docs.kenshi.io/services/audits/index.html" class="product">
      <Shield />
      <h3>Security Audits</h3>
      <Arrow />
    </a>
    <a
      href="https://docs.kenshi.io/services/development/index.html"
      class="product"
    >
      <Code />
      <h3>Blockchain Development</h3>
      <Arrow />
    </a>
  </div>
</div>

<div class="cards">
  <InfoCard
    image="/images/token.png"
    title="The Token"
    description="Looking for the ₭enshi token? The Kenshi token is a frictionless yield token that can provide a passive income to its holders, and that is also used to pay for the Kenshi services."
    buttons={[
      {
        href: "/swap",
        external: false,
        label: "Buy",
      },
      {
        href: "https://charts.bogged.finance/?c=bsc&t=0x42f9c5a27a2647a64f7D3d58d8f896C60a727b0f",
        external: true,
        label: "Charts",
      },
      {
        href: "https://docs.kenshi.io/token/tokenomics.html",
        external: false,
        label: "Learn more",
      },
    ]}
  />
  <InfoCard
    image="/images/pfp.png"
    title="Community"
    description="Join the Kenshi communities to talk tech, partake in early adopter programs, get help with one of our services, or to get the latest Kenshi news."
    buttons={[
      {
        href: "https://t.me/kenshi_token",
        external: true,
        label: "Telegram",
      },
      {
        href: "https://twitter.com/kenshi_token",
        external: true,
        label: "Twitter",
      },
      {
        href: "https://docs.kenshi.io/community.html",
        external: false,
        label: "More",
      },
    ]}
  />
</div>

<div class="getting-started">
  <div class="guides">
    <div class="guide">
      <div class="description">
        <h2>Getting started is easy.</h2>
        <h3>Use VRF to get randomness.</h3>
        <div class="content">
          <p>
            The Kenshi Verifiable Random Function (VRF) oracle can generate and
            verify pseudorandom numbers to be used by smart contracts on-chain.
          </p>
          <p>
            Enjoy a responsive VRF solution on BNB Smart Chain, Polygon, Fantom
            and Avalanche chains.
          </p>
        </div>
        <div class="spacer" />
        <div class="spacer" />
        <h4>Learn how to get a random number</h4>
        <div class="buttons">
          <Button
            solid
            href="https://remix.ethereum.org/#url=https://raw.githubusercontent.com/kenshi-token/d20/master/contracts/D20.sol"
            target="_blank"
          >
            Remix <External />
          </Button>
          <Button
            solid
            href="https://github.com/kenshi-token?q=vrf&type=all&language=&sort="
            target="_blank"
          >
            Github <External />
          </Button>
          <Button href="https://docs.kenshi.io/services/vrf/index.html">
            Docs <ChevronRight />
          </Button>
        </div>
      </div>
      <div class="sample">
        <Gist src="pouya-eghbali/2aba0069fa0cd8eded3c0df4d966232e" />
      </div>
    </div>
  </div>
</div>

<div class="deep-index">
  <div class="mask">
    <img src="/images/mask.elephant.png" alt="Mask" />
  </div>
  <div class="usages">
    <div class="title">
      <h2>All in one blockchain data solution.</h2>
    </div>
    <div class="grid">
      <Usage
        title="Push notifications for the blockchain"
        buttons={[
          {
            href: "https://github.com/kenshi-token?q=reverse-api+OR+graphql&type=public&language=&sort=",
            external: true,
            label: "View examples",
          },
        ]}
      >
        <BellOn />
        <Link />
        <ChartNetwork />
        <div slot="description">
          <p>
            Receive blockchain events directly on your AWS Lambda functions or
            HTTP reverse API endpoints.
          </p>
          <p>Focus on your product, we provide the data.</p>
        </div>
      </Usage>

      <Usage
        title="Never miss an event again"
        buttons={[
          {
            href: "https://blog.kenshi.io/introducing-the-kenshi-deep-blockchain-indexing-services-7fc4b159a946",
            external: true,
            label: "Learn more",
          },
        ]}
      >
        <Bolt />
        <CheckDouble />
        <div slot="description">
          <p>
            Kenshi scans each block multiple times to make sure no event is
            missed.
          </p>
          <p>Reliability for your services is key, you can count on us.</p>
        </div>
      </Usage>

      <Usage
        title="Fully managed, scales to infinity"
        buttons={[
          {
            href: "https://docs.kenshi.io/services/deep-index/index.html",
            external: false,
            label: "Start today",
          },
        ]}
      >
        <LayerPlus />
        <Infinity />
        <div slot="description">
          <p>
            Kenshi is a highly available, managed serverless solution that
            scales to infinity.
          </p>
          <p>Never worry about infrastructure again, we've got you covered.</p>
        </div>
      </Usage>
    </div>
  </div>
</div>

<div class="resources">
  <div class="grid">
    <CardButton
      href="https://github.com/kenshi-token"
      image="/images/pfp/github.png"
      title="Github"
      description="Check Kenshi GitHub repositories"
    />
    <CardButton
      href="https://www.npmjs.com/org/kenshi.io"
      image="/images/pfp/npm.png"
      title="NPM"
      description="See all Kenshi NPM packages"
    />
    <CardButton
      href="https://blog.kenshi.io"
      image="/images/pfp/medium.png"
      title="Medium"
      description="Read Kenshi blog articles"
    />
    <CardButton
      href="https://t.me/kenshi_developers"
      image="/images/pfp/telegram.png"
      title="Telegram"
      description="Join Kenshi developers chat"
    />
    <CardButton
      href="https://discord.gg/y4f5Rh5Apq"
      image="/images/pfp/discord.png"
      title="Discord"
      description="Join Kenshi Discord server"
    />
    <CardButton
      href="https://docs.kenshi.io"
      image="/images/pfp/docs.png"
      title="Docs"
      description="Read Kenshi documentation"
    />
  </div>
  <div class="details">
    <h2>Developer resources</h2>
    <div>
      Find examples, tools and documents for integrating the Kenshi products and
      services into your projects.
    </div>
  </div>
</div>

<div class="articles">
  <h2>Latest articles</h2>
  <div class="grid">
    <Article
      image="/images/medium/kenshi-deep-index.png"
      title="Kenshi Deep Indexing Service: Blazing fast blockchain data access."
      description="Getting events out of the blockchain seems like a trivial task at first. You might be using libraries such as ethers.js or web3.js."
      href="https://blog.kenshi.io/kenshi-deep-indexing-service-blazing-fast-blockchain-data-access-ceca261e8912"
    />
    <Article
      image="/images/medium/vrf.png"
      title="Kenshi VRF: 40% to infinitely faster than Chainlink."
      description="In this article, you’ll discover how the Kenshi VRF oracle compares with Chainlink."
      href="https://blog.kenshi.io/kenshi-vrf-40-to-infinitely-faster-than-chainlink-7856853a3ac1"
    />
  </div>
  <div class="buttons">
    <Button href="https://blog.kenshi.io/">
      View all articles <External />
    </Button>
  </div>
</div>

<Footer />

<style>
  .products {
    position: relative;
  }
  .mask {
    position: absolute;
    z-index: -1;
    height: 960px;
    top: -74%;
    padding: 0;
    opacity: 0.6;
  }
  .mask img {
    height: 100%;
  }
  .hero {
    padding: 6em;
    gap: 6em;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: calc(100vh - 66px);
    box-sizing: border-box;
    flex-wrap: wrap;
  }
  .hero .content {
    display: flex;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
    flex-direction: column;
    gap: 6em;
    flex: 3;
  }
  .hero .graphics {
    flex: 2;
    height: 100%;
    min-width: 300px;
    display: flex;
    justify-content: center;
  }
  .hero .graphics img {
    width: 540px;
    max-width: 80%;
    height: 100%;
    object-fit: contain;
  }
  @media only screen and (max-width: 880px) {
    .hero .buttons {
      justify-content: center;
    }
  }
  @media only screen and (max-width: 640px) {
    .hero .content {
      gap: 3em;
    }
    .hero .content .motto {
      font-size: 2em;
    }
    .hero {
      padding: 1em;
      padding-top: 2em;
      gap: 4em;
      height: auto;
      align-items: center;
    }
    .hero .graphics {
      display: flex;
      justify-content: center;
    }
  }
  .hero .logo {
    width: 440px;
    max-width: 90%;
  }
  .hero .motto {
    font-size: 3em;
    max-width: 90%;
    font-family: "Frank";
    text-align: center;
    font-weight: 500;
  }
  .buttons {
    display: flex;
    gap: 1em;
    flex-wrap: wrap;
  }
  .spacer {
    flex: 1;
  }
  .cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 4em;
    padding: 4em;
  }
  @media only screen and (max-width: 640px) {
    .cards {
      padding: 2em 1em;
      gap: 2em;
    }
  }
  .discover {
    padding: 2em 4em;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 4em;
  }
  @media only screen and (max-width: 640px) {
    .discover {
      padding: 2em 1em;
      gap: 2em;
    }
  }
  .discover h2 {
    font-size: 2em;
    margin: 0;
  }
  .discover .products-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 2em;
    padding: 0;
  }
  .discover .product {
    display: flex;
    gap: 0.75em;
    flex-direction: row;
    align-items: center;
    color: #000;
  }
  .discover .product h3 {
    margin: 0;
  }
  .discover .product :global(svg) {
    height: 1.25em;
  }
  .discover a:hover {
    color: var(--primary-color);
  }
  .discover a:hover :global(svg) {
    fill: var(--primary-color);
  }

  .products {
    padding: 4em;
    padding-bottom: 2em;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2em;
    width: 100%;
    box-sizing: border-box;
  }
  @media only screen and (max-width: 640px) {
    .products {
      padding: 2em 1em;
    }
    .products .start h2 {
      margin-top: 0.75em;
    }
  }
  .products .products-list {
    display: grid;
    gap: 2em;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  }
  .products > div {
    padding: 1em;
  }
  @media only screen and (max-width: 640px) {
    .products > div {
      padding: 0;
    }
  }

  .start h2 {
    margin-top: 0;
    font-size: 2em;
  }
  .articles {
    padding: 4em;
  }
  @media only screen and (max-width: 640px) {
    .articles {
      padding: 2em 1em;
    }
  }
  .articles h2 {
    font-size: 2em;
  }
  .articles .grid {
    margin-top: 4em;
    display: grid;
    grid-template-columns: repeat(
      auto-fill,
      minmax(280px, calc((100% - 6em) / 4))
    );
    gap: 2em;
  }
  .articles > .buttons {
    margin-top: 2em;
  }
  @media screen and (max-width: 1350px) {
    .articles .grid {
      grid-template-columns: repeat(
        auto-fill,
        minmax(280px, calc((100% - 2em) / 2))
      );
    }
  }
  @media only screen and (max-width: 720px) {
    .articles .grid {
      grid-template-columns: 1fr;
    }
  }

  .getting-started {
    padding: 4em;
  }
  @media only screen and (max-width: 640px) {
    .getting-started {
      padding: 2em 0.5em;
    }
    .getting-started h2,
    .getting-started h3 {
      margin-top: 0;
    }
    .getting-started .description {
      padding: 0 0.5em;
    }
  }
  .guides {
    display: flex;
    gap: 4em;
    width: 100%;
    flex-direction: column;
  }
  .guide {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, calc(50% - 2em)));
    gap: 4em;
  }
  @media screen and (max-width: 1320px) {
    .guide {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 100%));
      gap: 4em;
    }
    .guide .sample {
      padding: 0.5em;
    }
  }
  @media screen and (max-width: 600px) {
    .guide {
      gap: 2.5em;
    }
  }
  .guides h2 {
    font-size: 2em;
  }
  .guide .description {
    display: flex;
    flex-direction: column;
  }
  .guide .content {
    width: 80%;
    line-height: 1.2em;
    color: #222;
  }
  @media screen and (max-width: 1200px) {
    .guide .content {
      width: 100%;
    }
  }
  .guide .sample {
    height: 444px;
  }
  .resources {
    padding: 4em;
    display: grid;
    grid-template-columns: 4fr 2fr;
    gap: 4em;
  }
  @media only screen and (max-width: 640px) {
    .resources {
      padding: 2em 1em;
    }
  }
  .resources h2 {
    font-size: 2em;
    margin-bottom: 1em;
    margin-top: 0;
  }
  .resources .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
    gap: 2em;
    justify-content: right;
  }

  @media only screen and (max-width: 800px) {
    .resources .details {
      grid-row: 1;
    }
    .resources {
      grid-template-columns: 1fr;
      width: 100%;
      box-sizing: border-box;
    }
  }
  @media only screen and (max-width: 990px) {
    .mask {
      display: none;
    }
  }
  .deep-index {
    padding: 4em;
    position: relative;
  }
  @media only screen and (max-width: 640px) {
    .deep-index {
      padding: 2em 1em;
    }
  }
  .deep-index h2 {
    font-size: 2em;
  }
  .deep-index .mask {
    right: 0em;
  }
  .usages {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 4em;
  }
  .usages .grid {
    grid-column: span 3;
    display: grid;
    gap: 4em;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  }
  @media only screen and (max-width: 800px) {
    .usages .grid {
      grid-column: span 2;
    }
  }
  @media only screen and (max-width: 600px) {
    .usages {
      gap: 0;
    }
    .usages .grid {
      grid-column: span 1;
      gap: 2em;
    }
  }

  .usages h2 {
    margin-top: 0em;
    font-size: 2em;
  }
  .usages p:first-of-type {
    margin-top: 0;
  }
  .usages .description h3 {
    margin-top: 0;
  }

  @media only screen and (max-width: 600px) {
    .resources {
      gap: 2.5em;
    }
    .articles h2 {
      margin: 0;
    }
    .articles .grid {
      margin-top: 2em;
    }
  }
</style>
