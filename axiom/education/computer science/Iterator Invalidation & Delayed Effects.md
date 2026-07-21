Lets say you work on a project and you have to iterate over bullets to see if they collide.

```cpp
void sCollision(){
	EntityVec bullets;
	EntityVec tiles;
	
	for(auto& b : bullets)
		for(auto& t : tiles)
			if(Physics::IsCollision(b, t))
				bullets.erase(b);
}
```

This might look fine, but it isn't.
We are iterating over a vector bullets, but when we *erase* one bullet we change the vector, leading to undefined behaviour.
So what do we do, to fix this?

We can modify, like setting m_alive to false or something.
But Removing or Adding will lead to undefined behaviour.

Another way is called **Delayed Effects**:

>One way to avoid iterator invalidation is to delay the effects of actions that modify collections until it is safe to do so.

When is this safe time?

It is, when we are NOT iterating over it.

But how do we do this delayed effect?

We can mark the items we want to do something with.
And then only add or remove entities at the beginning of a frame *when it is safe.*

This is one easy way, but there are also others.

This can be done by for example an [[Entity Manager]].






