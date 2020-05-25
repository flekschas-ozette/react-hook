<hr>
<div align="center">
  <h1 align="center">
    useEvent()
  </h1>
</div>

<p align="center">
  <a href="https://bundlephobia.com/result?p=@react-hook/event">
    <img alt="Bundlephobia" src="https://img.shields.io/bundlephobia/minzip/@react-hook/event?style=for-the-badge&labelColor=24292e">
  </a>
  <a aria-label="Types" href="https://www.npmjs.com/package/@react-hook/event">
    <img alt="Types" src="https://img.shields.io/npm/types/@react-hook/event?style=for-the-badge&labelColor=24292e">
  </a>
  <!--
  <a aria-label="Code coverage report" href="https://codecov.io/gh/jaredLunde/react-hook">
    <img alt="Code coverage" src="https://img.shields.io/codecov/c/gh/jaredLunde/react-hook?style=for-the-badge&labelColor=24292e">
  </a>
  <a aria-label="Build status" href="https://travis-ci.com/jaredLunde/react-hook">
    <img alt="Build status" src="https://img.shields.io/travis/com/jaredLunde/react-hook?style=for-the-badge&labelColor=24292e">
  </a>
  -->
  <a aria-label="NPM version" href="https://www.npmjs.com/package/@react-hook/event">
    <img alt="NPM Version" src="https://img.shields.io/npm/v/@react-hook/event?style=for-the-badge&labelColor=24292e">
  </a>
  <a aria-label="License" href="https://jaredlunde.mit-license.org/">
    <img alt="MIT License" src="https://img.shields.io/npm/l/@react-hook/event?style=for-the-badge&labelColor=24292e">
  </a>
</p>

<pre align="center">npm i @react-hook/event</pre>
<hr>

A React hook for adding events to HTML elements. This hook cleans up your listeners
automatically when it unmounts. You won't have to worry about wrapping your
listener in a `useCallback()` because this hook makes sure your most recent callback
is always invoked.

## Quick Start

```jsx harmony
import * as React from 'react'
import useEvent from '@react-hook/event'

// Logs an event each time target.current is clicked
const Component = () => {
  const target = useRef(null)
  useEvent(target, 'click', (event) => console.log(event))
  return <div ref={target} />
}

// Logs an event each time the `document` is clicked
const DocumentComponent = () => {
  const target = useRef(null)
  useEvent(document, 'click', (event) => console.log(event))
  return <div ref={target} />
}

// Logs an event each time the `window` is clicked
const WindowComponent = () => {
  const target = useRef(null)
  useEvent(window, 'click', (event) => console.log(event))
  return <div ref={target} />
}
```

## API

### useEvent(target, type, listener)

```ts
const useEvent = <
  T extends HTMLElement = HTMLElement,
  K extends keyof HTMLElementEventMap = keyof HTMLElementEventMap
>(
  target: React.RefObject<T> | T | Window | Document | null,
  type: K,
  listener: EventListener<K>
)
```

| Argument | Type                                                                                     | Required? | Description                                                         |
| -------- | ---------------------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------- |
| target   | <code>React.RefObject&lt;T&gt; &#124; T &#124; Window &#124; Document &#124; null</code> | Yes       | The React ref, `window`, or `document` to add the event listener to |
| type     | `keyof HTMLElementEventMap`                                                              | Yes       | The type of event to listen for                                     |
| listener | `(this: HTMLElement, ev: HTMLElementEventMap[K]) => any`                                 | Yes       | The callback invoked when the event type fires                      |

## LICENSE

MIT