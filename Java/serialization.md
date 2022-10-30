# Serialization

Serialization is the conversion of the state of an object into a byte stream; deserialization does 
the opposite. Stated differently, serialization is the conversion of a Java object into a static 
stream (sequence) of bytes, which we can then save to a database or transfer over a network.

## Serializable interface

If you want a class object to be serializable, all you need to do it implement the 
`java.io.Serializable` interface. Serializable in java is a marker interface and has no
fields or methods to implement. It’s like an Opt-In process through which we make our classes
serializable. Serialization in java is implemented by `ObjectInputStream` and `ObjectOutputStream`,
so all we need is a wrapper over them to either save it to file or send it over the network.
