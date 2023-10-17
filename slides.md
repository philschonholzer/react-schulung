---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## React Schulung
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: React Schulung
mdc: true
---

# React Schulung

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Philip Schönholzer

- Entwickler bei Apptiva
- Fokus Requirements-Engineering und UX
- In den letzten 8 Jahren an über 10 React-Projekten gearbeitet
- Wohnhaft in Luzern
- Verheiratet, ohne Kinder
- Meine aktuelle Leidenschaft ist Sim-Racing

---
layout: default
---

# Agenda

<Toc maxDepth="1"></Toc>

---
transition: fade-out
---

# Warum React 

- 🚀 **Einfach zu starten** - Zu Beginn gibt es ein einfaches Konzept zu verstehen und man kann starten.
- 🧑‍💻 **Dev-Experience** - Entwicklung macht immer noch Spass, wenig Ärger, keine Probleme mit Updates.
- 🌱 **Functional** - Hatten jahrelang mit OOP gearbeitet und das Gras sieht auf der anderen Seite immer grüner aus.
- 🤹 **Vielseitig einsetzbar** - React(-Wissen) kann für vieles eingesetzt werden. Mobile Apps, Mail-Templates, 3D-Szenen, PDFs und natürlich Web.
- 😃 **Riesiges Ökosystem** - Packages, Frameworks, Lernmaterial, Videos, Entwickler:innen, Cloud-Angebote, UI-Frameworks, usw.

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
transition: fade-out
---

# Weshalb würde man etwas anderen wählen

- **Vue** - Möchte etwas wie Angular.js (v1.0) haben.
- **Svelte** - Möchte möglichst kleine JS-Bundles haben.
- **Angular** - Möchte viele Vorgaben haben.
- **Solid** - Mag React, möchte aber mit Signals arbeiten.
- **Preact** - Braucht bloss 90% von React, dafür kleinere Bundles haben.

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
transition: fade-out
---

# React Komponenten

Eine React Komponente ist eine Funktion die Properties als Parameter erhält und JSX zurück gibt.
<div grid="~ cols-2 gap-4">
<div>

## user-card.tsx

```tsx {10-17|1-9|all}
interface Props {
  user: {
    id: number
    firstName: string
    lastName: string
    role: string
  }
}

function UserCard({ user }: Props) {
  return (
    <div>
      <h3>{user.firstName} {user.lastName}</h3>
      <p>Rolle <span>{user.role}</span></p>
    </div>
  )
}
```

</div>
<div>
<div v-click>

## Input

```ts
{
  user: {
    id: 22,
    firstName: "Freddy",
    lastName: "Hauser",
    role: "Admin",
  }
}
```
</div>
<div v-click>
<br>

## Resultat (JSX)

```html
<div>
  <h3>Freddy Hauser</h3>
  <p>Rolle <span>Admin</span></p>
</div>
```
</div>
</div>

</div>

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
transition: fade-out
---

# React Komponenten

Eigene Komponenten wie andere HTML-Elemente nutzen. Eigene Komponenten gross schreiben.

<div grid="~ cols-2 gap-4">
<div>

## user-card.tsx

```tsx {10|all}
interface Props {
  user: {
    id: number
    firstName: string
    lastName: string
    role: string
  }
}

export default function UserCard({ user }: Props) {
  return (
    <div>
      <h3>{user.firstName} {user.lastName}</h3>
      <p>Rolle <span>{user.role}</span></p>
    </div>
  )
}
```

</div>
<div>
<div v-click="1">

## user-list.tsx nutzt UserCard

```tsx {1,12|all}
import UserCard from './user-card'

function UserList() {
  const user = {
    id: 22,
    firstName: "Freddy",
    lastName: "Hauser",
    role: "Admin",
  }
  return (
    <section>
      <UserCard user={user} />
    </section>
  )
}
```

</div>

</div>
</div>

<!--
Presenter note with **bold**, *italic*, and ~~striked~~ text.

Also, HTML elements are valid:
<div class="flex w-full">
  <span style="flex-grow: 1;">Left content</span>
  <span>Right content</span>
</div>
-->

---

# It's just JS

JSX ist JS. Wenn in einem Loop mehrere Elemente erstellt werden, muss ein Key gesetzt werden.

<div grid="~ cols-2 gap-4">
<div>

## React

```tsx {14-15|all}
//...
function UserList() {
  const users = [{
    id: 22,
    firstName: "Freddy",
    lastName: "Hauser",
    role: "Admin",
  }, 
  {/*...*/},
  {/*...*/}]
  return (
    <section>
      <h2>Users</h2>
      {users.map((user) => 
        <UserCart key={user.id} user={user} />)}
    </section>
  )
}
```
</div>
<div>
<div v-click="1">

## Resultat

```html
<section>
  <h2>Users</h2>
  <div>
    <h3>Freddy Hauser</h3>
    <p>Rolle <span>Admin</span></p>
  </div>
  <div>
    <h3>Fränzi Schilter</h3>
    <p>Rolle <span>CFO</span></p>
  </div>
  <div>
    <h3>Jessi Kramer</h3>
    <p>Rolle <span>CEO</span></p>
  </div>
</section>
```

</div>
</div>
</div>

<!--
Presenter note with **bold**, *italic*, and ~~striked~~ text.

Also, HTML elements are valid:
<div class="flex w-full">
  <span style="flex-grow: 1;">Left content</span>
  <span>Right content</span>
</div>
-->

---
transition: fade-out
---

# State

Muss sich eine Komponente einen Zustand merken, so nutzt man den useState-Hook.

```tsx {all|1,4|4-6|5-6,9-11|4,11|all}
import { useState } from 'react'

export default function Counter() {
  const [count, setCount] = useState(0)
  const inc = () => setCount((prev) => prev + 1)
  const dec = () => setCount((prev) => prev - 1)
  const oneMore = count + 1
  return (
    <div>
      <button onClick={inc}>+</button>
      <button onClick={dec}>-</button>
      <div>Count: {count}</div>
      <div>One higher: {oneMore}</div>
    </div>
  )
}
```


---
transition: fade-out
---

# Lifting State Up

Muss der Zustand in unterschiedlichen Komponenten bekannt sein, so sollte in zuerst versucht werden den Zustand zu "heben".

<div grid="~ cols-2 gap-4">
<div>

<div v-click="1">


```tsx {all|1,6|2-3,9-10|all}
import { useState } from 'react'
import ChangeCount from './change-count'
import ShowCount from './show-count'

export default function Counter() {
  const [count, setCount] = useState(0)
  return (
    <>
      <ChangeCount setCount={setCount} />
      <ShowCount count={count} />
    </>
  )
}
```

</div>
</div>
<div>

<div v-click="4">

```tsx {all|2,5|all}
interface ChangeCountProps {
  setCount: Function
}
export default function ChangeCount(
    {setCount}: ChangeCountProps
  ) {
  const inc = () => setCount((prev) => prev + 1)
  const dec = () => setCount((prev) => prev - 1)
  return (<div>
    <button onClick={inc}>+</button>
    <button onClick={dec}>-</button>
    </div>)
}
```

```tsx {all|2,4|all}
interface ShowCountProps {
  count: number
}
function ShowCount({ count }: ShowCountProps) {
  return <div>Count: {count}</div>
}

```

</div>
</div>
</div>

---
transition: fade-out
---

# Global State

**React Context**, **Redux Toolkit**, **Zustand**, **Xstate** und viele weitere mögliche Lösungen.

<div grid="~ cols-2 gap-4">
<div>

## Zustand Store erstellen

use-counter.ts

```ts
import { create } from 'zustand'

type CounterStore = {
  count: number
  increment: () => void
  decrement: () => void
}

const useCounter = create<CounterStore>()((set) => ({
  count: 0,
  increment: () => set((state) => 
    ({ count: state.count + 1 })),
  decrement: () => set((state) => 
    ({ count: state.count - 1 })),
}))

export default useCounter
```

</div>
<div>

## Zustand Store nutzen

counter-using-global-store.tsx

```tsx
import useCounter from './counterStore';

const CounterUsingGlobalStore = () => {
  const { count, increment, decrement } = useCounter();

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={decrement}>Decrement</button>
      <button onClick={increment}>Increment</button>
    </div>
  );
};
```

</div>
</div>
---

# Daten fetchen / State auf den Server halten

<div grid="~ cols-2 gap-8">
<div>

- `fetch` direkt in useEffect - besser Abstand nehmen
- TanStack Query - Sehr mächtig. Sehr beliebt. 
- SWR (Vercel) - Ähnlich wie TanStack Query
- RTQ (Redux Toolkit Query) - Teil von Redux Toolkit
- react-async-hook - Minimalistisch

</div>

<div>

<div v-click>

```ts
import { useQuery } from '@tanstack/react-query'

const queryFn = () => 
  fetch('/api/customers').then((res) => res.json())
export const useCustomers = () =>
  useQuery({ queryKey: ['customerData'], queryFn })
```

```tsx
import { useCustomers } from './use-customer'

function Example() {
  const { isLoading, error, data } = useCustomers()

  if (isLoading) return 'Loading...'

  if ({error}) 
    return `An error has occurred: ${error}`

  return (
    <div>
      <h1>Customers</h1>
      {data.map(c => <Customer key={c.id} data={c}/>)}
    </div>
  )
}
```

</div>
</div>
</div>

---

# Styling

<div grid="~ cols-2 gap-8">
<div>


## Technologie

React hat keine Vorgaben wie gestylet wird. Man kann `className` auf unterschiedliche Arten nutzen. Astro bietet das `<style>`-Tag.

- Tailwind - Pragmatisch und passt perfekt auf das Komponenten-Modell von Astro und React.
- CSS-Module - Funktioniert in Astro und React, aber umständlicher.
- `<style>` - Einfach, aber funktioniert nur in Astro-Komponenten.

</div>
<div v-click>

## UI-Library (React)

Fix-Fertige UI-Elemente, welche direkt genutzt werden können, wie Date-Picker, Dialoge, Switch-Buttons, usw.

- shadcn/ui - Übernehmen oder komplett umbauen und für die eigenen Bedürfnisse anpassen (viele Best-Practices).
- MUI - Grosse Sammlung von Elementen, welche grobe Anpassungen erlauben.
- Mantine - Ähnlich wie MUI.

</div>
</div>
---

# Struktur

- Co-Location
- Bei Apptiva hat (fast) jedes Projekt folgende Ordner
  - `modules` oder `domain` - Business-Logik
  - `adapters` - Schnittstellen (eigene Endpoints, third party APIs, usw.)
  - `components` - Globale Komponenten wie z.B. UI-Elemente
  - `scenes`, `pages` oder `app` - Aufteilung der Seiten/Szenen mit ihren spezifischen Komponenten (Abhängig vom Framework) 

---

# Testing

## Unit-Test

- Test-Framework wie Jest, Vitest
- React-Komponenten mit Testing-Library testen

## E2E-Test

- PlayWright oder Cypress

---

# Astro

- SSG mit Island Architektur
- Kann mit unterschiedlichen UI-Libraries umgehen
- Liefert standardmässig kaum JS aus
- Sehr einfach zu nutzen und gute DX

---

# SSG vs SSR

|                 | SSG             | SSR             |
|-----------------|-----------------|-----------------|
| Bedeutet        | Static Site Generated | Server Side Rendered |
| HTML-Generierung | Zur Build-Zeit | Auf Anfrage (+ Cache) |
| TTFP (first paint) | Extrem schnell | Abhängig vom Daten- und Rechenbedarf  |
| Inhaltl. Änderungen  | Neuer Build der Seite oder Seiten nötig | Mit der nächsten Anfrage  |
| Sicherheit | Extrem hoch | Datenquelle muss sicher sein |
| Energiebedarf kleiner | Je weniger Änderungen  | Je weniger Anfragen oder CPU |
| Verfügbarkeit | Extrem hoch  | Ist schwieriger zu gewährleisten |


---

# Nächstes Mal

- Seite in Astro erstellen: Deep Dive

Weitere mögliche Themen:

- React-Hooks genauer anschauen (wie useState, useEffect, usw.)
- Visuelles Testing einer Seite / Komponente (automatisiert)
- FE Architektur Islands Architecture
- Trends & Best practices
- Einzelne Repos vs Monorepo

Was vertiefen? Andere Themen?
