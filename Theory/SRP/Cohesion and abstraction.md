### Summary
Cohesion determines the degree to which two modules belong to each other. If the abstraction level matches, then it is good design.

### Notes

**Yordon and constantine** marked on the cohesion. This is defined by the degree to which two modules belong to together. It can be taken as a measure of the strength of relationshop between the class' methods and the data themselves. **The abstraction level of these two should match**

eg: The following example showcases where `giveFuelToEngine` does not match the abstraction level of the other methods.
```
class Car  
{  
public function __construct()  
{...}  
  
public function drive()  
{...}  
  
public function giveFuelToEngine()  
{...}  
}
```

