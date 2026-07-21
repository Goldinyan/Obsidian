---
id: Queries lesen - React
aliases:
Topic: How to read date from url queries.
Related:
  - "[[%Web]]"
  - "[[%React]]"
Tags:
  - w
Date: 2026-05-03T19:09:00
Updated:
Source:
---
# Queries lesen - React

```ts
interface Props {
  searchParams: {
    x?: string;
  };
}

export default function Page({ searchParams }: Props) {
  return (
    <div>
      <h1>Query x: {searchParams.x}</h1>
    </div>
  );
}
```