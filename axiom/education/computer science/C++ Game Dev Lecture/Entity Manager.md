

An Entity Managers main function is to separate logic from data. 
An Entity Manager handels Entity creation and destruction.
This should work in a way in which the logic just gets the data and does not have to think about, if it is a vector or a set or anything else.

A Entity Manger should look along the lines of this:

```cpp
typedef std::vector<std::shared_ptr<Entity>> EntityVec;
typedef std::map <std::string, EntityVec> EntityMap;

class EntityManager {

public:
	EntityManger();
	void update(); // to handle creation of m_toAdd
	std::shared_ptr<Entity> addEntity(const std::string& tag); // places entity into m_toAdd, only after update its there
	EntityVec& getEntities();
	EntityVec& getEntities(const std::string& tag); // tag can also be an enum for better efficency
	
private:
	EntityVec m_entities; 
	EntityVec m_toAdd; // to work against [[Iterator Invalidation & Delayed Effects]], its like a waiting room
	EntityMap m_entityMap; // This doubles the amount of pointers
	// but allows us to write easier and faster code
	size_t m_totalEntities{0};
}

```




### Adding Entities


```cpp
std::shared_ptr<Entity> EntityManager::addEntity(const std::string& tag)
{
  // give each entity an increading size_t id
  auto e = std::make_shared<Entity>(tag, m_totalEntities++);
  // add to waiting room instead of vector instantly
  m_toAdd.push_back(e);
  return e;
}
```


### EntityManager Update