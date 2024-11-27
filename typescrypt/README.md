# Node

# Interoperabilidade entre Node.js e C

Este documento descreve como integrar código C com Node.js para melhorar o desempenho de aplicações JavaScript.

## Introdução

Node.js permite a interoperabilidade com bibliotecas C através de módulos nativos. Isso é útil para operações que exigem alto desempenho.

## Passos para integração

1. **Escreva o código C**: Crie uma biblioteca C com as funções que deseja expor para o Node.js.
2. **Compile a biblioteca**: Compile o código C em uma biblioteca compartilhada (.so, .dll, .dylib).
3. **Use `ffi-napi`**: Utilize o pacote `ffi-napi` no Node.js para carregar e chamar funções da biblioteca C.

## Exemplo

### Código C

```c
// exemplo.c
#include <stdio.h>

void hello() {
    printf("Hello from C!\n");
}
```

### Compilação

```sh
gcc -shared -o exemplo.so -fPIC exemplo.c
```

### Código Node.js

```javascript
const ffi = require("ffi-napi");

const lib = ffi.Library("./exemplo.so", {
  hello: ["void", []],
});

lib.hello(); // Output: Hello from C!
```

## Conclusão

Integrar Node.js com C pode melhorar significativamente o desempenho de aplicações que exigem processamento intensivo.

# Deno

## Interoperabilidade entre Deno e C

Deno, assim como Node.js, permite a interoperabilidade com bibliotecas C para melhorar o desempenho de aplicações JavaScript.

## Passos para integração

1. **Escreva o código C**: Crie uma biblioteca C com as funções que deseja expor para o Deno.
2. **Compile a biblioteca**: Compile o código C em uma biblioteca compartilhada (.so, .dll, .dylib).
3. **Use `Deno.dlopen`**: Utilize a função `Deno.dlopen` para carregar e chamar funções da biblioteca C.

## Exemplo

### Código C

```c
// exemplo.c
#include <stdio.h>

void hello() {
    printf("Hello from C!\n");
}
```

### Compilação

```sh
gcc -shared -o exemplo.so -fPIC exemplo.c
```

### Código Deno

```javascript
const lib = Deno.dlopen("./exemplo.so", {
  hello: { parameters: [], result: "void" },
});

lib.symbols.hello(); // Output: Hello from C!
```

## Conclusão

Integrar Deno com C pode melhorar significativamente o desempenho de aplicações que exigem processamento intensivo.

# Interoperabilidade entre Deno e Rust

Deno também permite a interoperabilidade com bibliotecas Rust para melhorar o desempenho de aplicações JavaScript.

## Passos para integração

1. **Escreva o código Rust**: Crie uma biblioteca Rust com as funções que deseja expor para o Deno.
2. **Compile a biblioteca**: Compile o código Rust em uma biblioteca compartilhada (.so, .dll, .dylib).
3. **Use `Deno.dlopen`**: Utilize a função `Deno.dlopen` para carregar e chamar funções da biblioteca Rust.

## Exemplo

### Código Rust

```rust
// exemplo.rs
#[no_mangle]
pub extern "C" fn hello() {
    println!("Hello from Rust!");
}
```

### Compilação

```sh
rustc --crate-type cdylib -o exemplo.so exemplo.rs
```

### Código Deno

```javascript
const lib = Deno.dlopen("./exemplo.so", {
  hello: { parameters: [], result: "void" },
});

lib.symbols.hello(); // Output: Hello from Rust!
```

## Conclusão

Integrar Deno com Rust pode melhorar significativamente o desempenho de aplicações que exigem processamento intensivo.

# Bun

## Interoperabilidade entre Bun e C

Bun, assim como Node.js e Deno, permite a interoperabilidade com bibliotecas C para melhorar o desempenho de aplicações JavaScript.

## Passos para integração

1. **Escreva o código C**: Crie uma biblioteca C com as funções que deseja expor para o Bun.
2. **Compile a biblioteca**: Compile o código C em uma biblioteca compartilhada (.so, .dll, .dylib).
3. **Use `bun:ffi`**: Utilize o pacote `bun:ffi` para carregar e chamar funções da biblioteca C.

## Exemplo

### Código C

```c
// exemplo.c
#include <stdio.h>

void hello() {
    printf("Hello from C!\n");
}
```

### Compilação

```sh
gcc -shared -o exemplo.so -fPIC exemplo.c
```

### Código Bun

```javascript
import { dlopen, FFIType } from "bun:ffi";

const lib = dlopen("./exemplo.so", {
  hello: { args: [], returns: FFIType.void },
});

lib.symbols.hello(); // Output: Hello from C!
```

## Conclusão

Integrar Bun com C pode melhorar significativamente o desempenho de aplicações que exigem processamento intensivo.
