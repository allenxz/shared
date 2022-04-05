> 题目来自：https://github.com/type-challenges/type-challenges



##  热身

### Hello World

```ts
type HelloWorld = string
```



## 简单

### 实现Pick

```ts
type MyPick<T, K extends keyof T> = {
  [key in K]: T[key]
}
```

### 实现 Readonly

```ts
type MyReadonly<T> = {
  readonly [key in keyof T]: T[key]
}
```

### 元组转换为对象

```ts
type TupleToObject<T extends readonly string[]> = {
  [val in T[number]]: val
}
```

### 第一个元素

```ts
type First<T extends any[]> = T extends [] ? never : T[0]
```

### 获取元组长度

```ts
type Length<T extends readonly any[]> = T['length']
```

### Exclude

这里主要是利用了`Distributive conditional types`的特性，详细[可戳](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-8.html#distributive-conditional-types)

```ts
type MyExclude<T, U> = T extends U ? never: T
```

### Awaited

```ts
type MyAwaited<T extends Promise<unknown>> = T extends Promise<infer U> 
  ? U extends Promise<unknown> 
    ? MyAwaited<U> 
    : U
  : never
```

### If

```ts
type If<C extends true | false, T, F> = C extends true ? T : F
```

### Concat

```ts
type Concat<T extends unknown[], U extends unknown[]> = [...T, ...U]
```

### Includes

```ts
type Includes<T extends readonly unknown[], U> =
  T extends [infer First, ...infer Rest]
    ? Equal<First, U> extends true ? true : Includes<Rest, U>
    : false;
```

### Push

```ts
type Push<T extends unknown[], U> = [U] extends T[number] ? T : [...T, U]
```

### Unshift

```ts
type Unshift<T extends unknown[], U> = [U, ...T]
```

### Parameters

```ts
type MyParameters<T extends (...args: any[]) => any> = T extends (...args: infer A) => any ? A : never
```



## 中等



## 困难



## 地狱

