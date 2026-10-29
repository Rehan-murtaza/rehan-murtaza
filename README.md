<!-- Header banner -->
<p align="center">
  <img width="100%" alt="Muhammad Rehan" src="https://capsule-render.vercel.app/api?type=waving&color=0:14365a,100:4d8fcc&height=170&section=header&text=Muhammad%20Rehan&fontSize=42&fontColor=ffffff&fontAlignY=40&desc=React.js%20Developer%20%7C%20Real-Time%20Trading%20%26%20Analytics%20Interfaces&descSize=16&descAlignY=62" />
</p>

<p align="center">
  <a href="https://github.com/Rehan-murtaza"><img src="https://komarev.com/ghpvc/?username=Rehan-murtaza&label=Profile%20views&color=1f4e79&style=flat" alt="Profile views" /></a>
  <a href="https://www.linkedin.com/in/muhammad-rehan-8844ab193/"><img src="https://img.shields.io/badge/LinkedIn-Muhammad%20Rehan-1f4e79?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:r.kmughal66@gmail.com"><img src="https://img.shields.io/badge/Email-r.kmughal66%40gmail.com-1f4e79?style=flat&logo=gmail&logoColor=white" alt="Email" /></a>
  <img src="https://img.shields.io/badge/Based%20in-Lahore%2C%20Pakistan-1f4e79?style=flat" alt="Location" />
</p>

---

## 👋 About Me

React.js developer with **3+ years of experience** building responsive web apps, **real-time trading dashboards**, financial charting interfaces, and analytics platforms. I enjoy the hard front-end problems: high-frequency WebSocket data, complex state, and UIs that stay fast under load.

- 🔭 Currently building at **Rocco Video**: live-streaming products, crypto-exchange terminals, and admin dashboards
- ⚡ Focus areas: **WebSocket performance**, **Redux architecture for high-frequency data**, **TradingView / Lightweight Charts**
- 🌱 Learning **Node.js & Express.js** to grow into a full-stack JavaScript developer
- 🤝 Open to collaborating on React, real-time, and fintech UI projects
- 📫 Reach me at **r.kmughal66@gmail.com**

---

## 🛠️ Tech Stack

<p>
  <img src="https://skillicons.dev/icons?i=js,react,redux,html,css,tailwind,mui,bootstrap&theme=dark" alt="Frontend" />
</p>
<p>
  <img src="https://skillicons.dev/icons?i=nodejs,express,firebase,git,github,postman,vite,npm,figma&theme=dark" alt="Tools" />
</p>

| Area | What I use |
| :-- | :-- |
| **Frontend** | JavaScript (ES6+), React.js, Tailwind CSS, Material UI, Bootstrap, styled-components |
| **State & Architecture** | Redux Toolkit, Context API, Zustand, custom hooks, memoized selectors |
| **Real-Time & APIs** | WebSockets, Socket.IO, REST APIs, Axios, token auth, KuCoin API |
| **Charts & Trading UI** | TradingView Charts, Lightweight Charts, ApexCharts, Chart.js, order books, depth charts, SMA / EMA / RSI / MACD / Bollinger Bands |
| **Performance** | Throttling, batched updates, Web Workers, re-render control |

---

## 🚀 Featured Work

> Most of my professional projects are built for companies and clients, so their code is private. Here is what I have worked on:

| Project | What it is | Tech |
| :-- | :-- | :-- |
| **Exbeast** | Crypto exchange front end with real-time order books, tickers, depth and candlestick charts, and KuCoin API integration | React, Redux Toolkit, WebSockets, Web Workers, TradingView Charts |
| **Exbotix** | Trading and analytics platform covering spot and futures workflows, leverage and margin modes, TP/SL, indicators, and bot interfaces | React, Redux Toolkit, WebSockets, Lightweight Charts, Tailwind |
| **[Profit Miner](https://profitminer.pro/)** | Crypto mining insights dashboard with live stats, earnings, and performance analytics | React, Chart.js, Material UI |
| **[Rocco](https://roccoexpert.com/)** | High-performance live-streaming platform with broadcast and viewer modes | React, Bootstrap |
| **Jokerz** | Short-video and live-streaming app with an admin dashboard | React, Material UI |
| **Gold Bazar** | Gold-selling platform with product catalog, price tracking, and order management | React, REST APIs |

---

## ⚡ How I Handle High-Frequency Data

A small pattern I rely on: buffer WebSocket ticks and flush them once per animation frame, so thousands of messages per second become at most one render per frame.

```js
import { useEffect, useRef } from "react";

// Batches incoming ticks and flushes them once per frame.
export function useBatchedFeed(socket, onFlush) {
  const buffer = useRef([]);
  const flushRef = useRef(onFlush);
  flushRef.current = onFlush;

  useEffect(() => {
    let raf;
    const onMessage = (e) => buffer.current.push(JSON.parse(e.data));
    const flush = () => {
      if (buffer.current.length) {
        flushRef.current(buffer.current);
        buffer.current = [];
      }
      raf = requestAnimationFrame(flush);
    };

    socket.addEventListener("message", onMessage);
    raf = requestAnimationFrame(flush);
    return () => {
      socket.removeEventListener("message", onMessage);
      cancelAnimationFrame(raf);
    };
  }, [socket]);
}
```

Paired with a Redux layout that keeps **ephemeral market feeds** separate from **persistent wallet and order state**, so a price tick never re-renders the whole app.

---

## 📈 Currently

- Building real-time trading and streaming interfaces at **Rocco Video**
- Learning **Node.js + Express.js** for full-stack JavaScript
- Exploring Web Worker based data pipelines for heavy order-book updates

---

## 🌐 Let's Connect

<p>
  <a href="https://www.linkedin.com/in/muhammad-rehan-8844ab193/"><img src="https://img.shields.io/badge/LinkedIn-Connect-1f4e79?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="mailto:r.kmughal66@gmail.com"><img src="https://img.shields.io/badge/Email-Say%20hello-1f4e79?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
  <a href="https://profitminer.pro/"><img src="https://img.shields.io/badge/Live-profitminer.pro-1f4e79?style=for-the-badge" alt="Profit Miner" /></a>
  <a href="https://roccoexpert.com/"><img src="https://img.shields.io/badge/Live-roccoexpert.com-1f4e79?style=for-the-badge" alt="Rocco" /></a>
</p>

<img width="100%" alt="footer" src="https://capsule-render.vercel.app/api?type=waving&color=0:4d8fcc,100:14365a&height=90&section=footer" />
