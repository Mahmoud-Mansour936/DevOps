# Array

```bash
# to define array
Array= ( "val_0" , "val_1" , "val_2" ) -> array type from its values' type

# to call value of it 
${Array[i]} --> with its index  

# use it in for loops 
for index in ${Array[@]} # @ sign means all values in array
do 
# logic 
echo $index
done 
```