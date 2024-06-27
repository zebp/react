
## Input

```javascript
import { useState } from "react"; // @enableChangeDetectionForDebugging

function useOther(x) {
  return x;
}

function Component(props) {
  const w = f(props.x);
  const z = useOther(w);
  const [x, _] = useState(z);
  return <div>{x}</div>;
}

function f(x) {
  return x;
}

export const FIXTURE_ENTRYPOINT = {
  fn: Component,
  params: [{ x: 42 }],
  isComponent: true,
};

```

## Code

```javascript
import { $structuralCheck } from "react-compiler-runtime";
import { c as _c } from "react/compiler-runtime";
import { useState } from "react"; // @enableChangeDetectionForDebugging

function useOther(x) {
  return x;
}

function Component(props) {
  const $ = _c(4);
  let t0;
  t0 = f(props.x);
  let condition42 = $[0] !== props.x;
  if (!condition42) {
    let old$t0 = $[1];
    $structuralCheck(old$t0, t0, "t0", "Component", "cached", "(8:8)");
  }
  $[0] = props.x;
  $[1] = t0;
  if (condition42) {
    const t041idem = f(props.x);
    $structuralCheck($[1], t041idem, "t0", "Component", "recomputed", "(8:8)");
  }
  const w = t0;
  const z = useOther(w);
  const [x] = useState(z);
  let t1;
  t1 = <div>{x}</div>;
  let condition44 = $[2] !== x;
  if (!condition44) {
    let old$t1 = $[3];
    $structuralCheck(old$t1, t1, "t1", "Component", "cached", "(11:11)");
  }
  $[2] = x;
  $[3] = t1;
  if (condition44) {
    const t143idem = <div>{x}</div>;
    $structuralCheck(
      $[3],
      t143idem,
      "t1",
      "Component",
      "recomputed",
      "(11:11)",
    );
  }
  return t1;
}

function f(x) {
  return x;
}

export const FIXTURE_ENTRYPOINT = {
  fn: Component,
  params: [{ x: 42 }],
  isComponent: true,
};

```
      