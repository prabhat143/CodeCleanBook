# Chapter 08 - Boundaries

How to integrate code with 3rd-party or open-source software.

### Using Third-Party Code
The natural tension between provider/user of an interface. Provider => focus on wide audience. User => focus on their particular needs. 

Example: java.util.Map Map is an interface with many methods: clear, containsKey, contains value, get, isEmpty, put, putAll, remove, size... It is
very flexible, any user can add items of any type to any Map.

If we need a Map of Sensors you can create something like:
```
// Without generics
Map sensors = new HashMap();
Sensor s = (Sensor) sensors.get(sensorId);
// With generics:
Map<Sensor> sensors = new HashMap<Sensor>();
Sensor s = sensors.get(sensorId);
```

This is not clean code. If you use instances of Map in your system if the Map Interface changes you will have to change a lot of references. 
Try to encapsulate any boundary interface like Map inside the class:
```
public class Sensor {
  private Map sensors = new HashMap();
  public Sensor getById(String id) {
    return (Sensor) sensor.get(id);
} }
```
Avoid returning it or accepting it as an argument in public APIs.

### Exploring and Learning Boundaries
Learning tests instead of experimenting and trying out the new stuff in our production code, we could write some tests to explore our understanding of the third-party code.
Learning Tests Are Better Than Free

Since you have to learn the 3rd party code anyway, learning tests are an easy way to learn and future-proof use of the API. With each release comes a new risk => we run the learning tests to see the changes.

These boundary tests ease the migration so that we don't have to stay with the old version longer than we should.

### Using Code That Does Not Yet Exist
Sometimes you have boundaries in your system that represents things that have not been designed yet.

You can create your own interface with the idea of how this should work and implement a Fake implementation for testing purposes. See the Adapter pattern.

### Clean Boundaries
When we use code that is out of our control special care must be taken to protect our investment and make sure future change is not too costly. 
Wrap them or use an Adapter to convert from our perfect interface to the provided interface.
