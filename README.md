# reactive-components
> Reactive React components, powered by @vue/reactivity.

```
yarn add @jas-chen/reactive-components
```

Clock example

```js
import React, { useMemo } from "react";
import { ref } from "@vue/reactivity";
import R, { Effect } from "@jas-chen/reactive-components";

const App = () => {
  return useMemo(() => {
    const time$ = ref(new Date().toLocaleTimeString());
    let intervalId;

    return (
      <>
        <Effect>
          {() => {
            intervalId = setInterval(() => {
              time$.value = new Date().toLocaleTimeString();
            }, 1000);

            return () => clearInterval(intervalId);
          }}
        </Effect>
        <R>{time$}</R>
      </>
    );
  });
};

export default App;
```