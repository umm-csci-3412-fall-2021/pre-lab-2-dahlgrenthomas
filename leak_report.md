# Leak report

A memory leak is caused by the is_clean function since it calls 
upon the strip function and that function returns an array. The array
needs to be cleaned after is_clean calls on it since is_clean returns
a boolean and not the array used. So I've added a free(cleaned) to 
is_clean to free up the memory. Since this array might be an empty 
string it is necesarry to check that it isn't an empty string before 
freeing the memory to avoid an error.