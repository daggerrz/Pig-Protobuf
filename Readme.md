# Pig Protocol Buffers support #

This is very stripped down version of Twitter's Elephant-Bird support for protocol buffers.
The main objective is to quickly provide protobuf support for Pig 0.9.0. Porting all of
the original Elephant-Bird to 0.9.0 is a major effort.

* Pig 0.9.0-SNAPSHOT compatible
* Only support for Protocol Buffers
* The "deprecated" code generation classes for protobufs is completely removed
* Maven build

##### How to use #####

DEFINE AddressBook com.twitter.elephantbird.pig.piggybank.ProtobufBytesToTuple('com.twitter.data.proto.tutorial.AddressBookProtos.AddressBook');
raw = LOAD  ...

addressbooks = FOREACH raw GENERATE AddressBook($1) as proto;
name = FOREACH addressbooks GENERATE FLATTEN(proto.person.name) as names;
