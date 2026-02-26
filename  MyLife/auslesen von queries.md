---
id: "auslesen von queries"
aliases:
Topic:
Related:
Tags:
  - w
Date:
Updated:
Source:
---
# auslesen von queries

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