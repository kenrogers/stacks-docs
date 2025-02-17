---
title: Palabras clave
description: Vea una lista detallada de todas las palabras clave para el lenguaje Clarity.
tags:
  - clarity
---

![](/img/keywords.jpg)
## Referencia de palabra clave

Detailed list of all keywords for the Clarity language.


### contract-caller
#### salida: `principal`
#### descripción:
Returns the caller of the current contract context. If this contract is the first one called by a signed transaction, the caller will be equal to the signing principal. If `contract-call?` was used to invoke a function from a new contract, `contract-caller` changes to the _calling_ contract's principal. If `as-contract` is used to change the `tx-sender` context, `contract-caller` _also_ changes to the same contract principal.
#### ejemplo:
```clarity
(print contract-caller) ;; Will print out a Stacks address of the transaction sender
```

### tx-sender
#### salida: `principal`
#### descripción:
Returns the original sender of the current transaction, or if `as-contract` was called to modify the sending context, it returns that contract principal.
#### ejemplo:
```clarity
(print tx-sender) ;; Will print out a Stacks address of the transaction sender
```

### block-height
#### output: `uint`
#### descripción:
Returns the current block height of the Stacks blockchain as an uint
#### ejemplo:
```clarity
(> block-height 1000) ;; returns true if the current block-height has passed 1000 blocks.
```

### burn-block-height
#### output: `uint`
#### descripción:
Returns the current block height of the underlying burn blockchain as a uint
#### ejemplo:
```clarity
(> burn-block-height 1000) ;; returns true if the current height of the underlying burn blockchain has passed 1000 blocks.
```

### none
#### output: `(optional ?)`
#### descripción:
Represents the _none_ option indicating no value for a given optional (analogous to a null value).
#### ejemplo:
```clarity
(define-public (only-if-positive (a int))
  (if (> a 0)
      (some a)
      none))
(only-if-positive 4) ;; Returns (some 4)
(only-if-positive (- 3)) ;; Returns none
```

### true
#### output: `bool`
#### descripción:
Boolean true constant.
#### ejemplo:
```clarity
(and true false) ;; Evaluates to false
(or false true)  ;; Evaluates to true
```

### false
#### output: `bool`
#### descripción:
Boolean false constant.
#### ejemplo:
```clarity
(and true false) ;; Evaluates to false
(or false true)  ;; Evaluates to true
```

### stx-liquid-supply
#### output: `uint`
#### descripción:
Returns the total number of micro-STX (uSTX) that are liquid in the system as of this block.
#### ejemplo:
```clarity
(print stx-liquid-supply) ;; Will print out the total number of liquid uSTX
```

### is-in-regtest
#### output: `bool`
#### descripción:
Returns whether or not the code is running in a regression test
#### ejemplo:
```clarity
(print is-in-regtest) ;; Will print 'true' if the code is running in a regression test
```

