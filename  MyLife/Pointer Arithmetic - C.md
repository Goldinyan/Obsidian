```c
typedef struct Person {
	char name[64];
	int age;
} person_t

int main(int argc, char *argv[]){
	person_t people[100]; // Array of 100 of people
	persont_t *p_person = &people 
	// is the adress of the base of people
	// people[0]
	
	// If we want to iterate over all people
	// most would do this:
	
	for(int i = 0; i < 100; i++){
		p_person->age = 0;
		
		p_person += sizeof(person_t)
	}
	
	// Makes sense, right?
	// We increase by the size of the struct person 
	// to get to the new Index
	
	// This will crash your programm, because
	// the compiler already knows what you are talking about
	// and this will get it to multiple sizeof(person) * sizeof(person)
	
	// Right would be:
	
	for(int i = 0; i < 100; i++){
		p_person->age = 0;
		
		p_person += 1;
		
		// or
		
		p_person++;
	}
	
	// This will work because the compiler knows
}
```