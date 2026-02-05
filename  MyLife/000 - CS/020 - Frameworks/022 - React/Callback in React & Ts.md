---
id: "Callback in React & Ts"
aliases:
Topic:
Related:
Tags:
  - w
Date:
Updated:
---
# Callback in React & Ts

A callback is used to change states of a parental component in a kids component.
It works by giving the children function a function as a prop, like this:

```ts

export default function ParentComponent() {
	const [value, setValue] = useState<number>(0);
	
	return (
		<ChildrenComponent
		
	)
}
interface ChildrenComponentProps {
  callback: (value: int) => void;
  value: int;
}


function ChildernComponent({ callback, value} : ChildrenComponentProps) {
	callback(1);
}
```