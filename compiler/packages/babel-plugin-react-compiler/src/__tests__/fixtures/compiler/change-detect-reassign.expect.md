
## Input

```javascript
// @enableChangeDetectionForDebugging
function Component(props) {
  let x = null;
  if (props.cond) {
    x = [];
    x.push(props.value);
  }
  return x;
}

```

## Code

```javascript
import { $structuralCheck } from "react-compiler-runtime";
import { c as _c } from "react/compiler-runtime"; // @enableChangeDetectionForDebugging
function Component(props) {
  const $ = _c(2);
  let x = null;
  if (props.cond) {
    x = [];
    x.push(props.value);
    let condition37 = $[0] !== props.value;
    if (!condition37) {
      let old$x = $[1];
      $structuralCheck(old$x, x, "x", "Component", "cached", "(3:6)");
    }
    $[0] = props.value;
    $[1] = x;
    if (condition37) {
      const x32idem = [];
      x32idem.push(props.value);
      $structuralCheck($[1], x32idem, "x", "Component", "recomputed", "(3:6)");
    }
  }
  return x;
}

```
      