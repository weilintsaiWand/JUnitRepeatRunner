# JUnitRepeatRunner
How to run JUnit repeately

# Basic idea 
http://stackoverflow.com/questions/1492856/easy-way-of-running-the-same-junit-test-over-and-over
In this case, if we have a test contains A/B/C (assumed in order).
By applying this approach. We can run all the test repeatly (again, in order)

# What if we want to ran unit tests repeatly with random order
One way is to hack Parameterized.java
In this project I copy the original code from JUnit 4.8.2
https://github.com/junit-team/junit/blob/fc7acc64dbbf5c28ef4bd3b142e35922d6294428/src/main/java/org/junit/runners/Parameterized.java
and did some modification to become ```RandParameterized.java```
The modification include

1. Add some code for Giraffa because this task is for Giraffa Testing originally
2. Add 

''' java
protected java.util.List<org.junit.runners.model.FrameworkMethod> computeTestMethods() {
   java.util.List<org.junit.runners.model.FrameworkMethod> methods = super.computeTestMethods();
   Collections.shuffle(methods);
   return methods;
}
```

