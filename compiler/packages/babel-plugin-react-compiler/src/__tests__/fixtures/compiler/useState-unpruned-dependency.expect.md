
## Input

```javascript
import { useState } from "react"; // @enableChangeDetectionForDebugging

function Component(props) {
  const w = f(props.x);
  const [x, _] = useState(w);
  return (
    <div>
      {x}
      {w}
    </div>
  );
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

function Component(props) {
  const $ = _c(5);
  let t0;
  t0 = f(props.x);
  let condition34 = $[0] !== props.x;
  if (!condition34) {
    let old$t0 = $[1];
    $structuralCheck(old$t0, t0, "t0", "Component", "cached", "(4:4)");
  }
  $[0] = props.x;
  $[1] = t0;
  if (condition34) {
    const t033idem = f(props.x);
    $structuralCheck($[1], t033idem, "t0", "Component", "recomputed", "(4:4)");
  }
  const w = t0;
  const [x] = useState(w);
  let t1;

  t1 = (
    <div>
      {x}
      {w}
    </div>
  );
  let condition36 = $[2] !== x || $[3] !== w;
  if (!condition36) {
    let old$t1 = $[4];
    $structuralCheck(old$t1, t1, "t1", "Component", "cached", "(7:10)");
  }
  $[2] = x;
  $[3] = w;
  $[4] = t1;
  if (condition36) {
    const t135idem = (
      <div>
        {x}
        {w}
      </div>
    );
    $structuralCheck($[4], t135idem, "t1", "Component", "recomputed", "(7:10)");
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
      