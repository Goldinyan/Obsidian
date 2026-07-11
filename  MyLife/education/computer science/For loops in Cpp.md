```cpp

int main(void){

	std::vector<int> v;
	
	for(int i = 0; i < v.size(); i++)
	{}

	// BAD
	
	for(size_t i{}; i < v.size(); ++i)
	{}

	// BETTER BUT STILL A LOT TO DO
	
	for(auto i{0uz}; i < v.size; ++i)
	{}
	
	// NEARLY PERFECT
	
	
	for(auto{v.size()}; i-- > 0;)
	{}
	
	// PERFECT

}



```