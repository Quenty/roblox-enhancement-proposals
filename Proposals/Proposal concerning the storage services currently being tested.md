# Proposal concerning the storage services currently being tested

For a long time, the lighting service has been used on ROBLOX to store objects. This is semantically incorrect, but since the lighting offered a static environment where all objects except skybox objects had no effect, this was regarded as an acceptable solution. However, this is still semantically incorrect and does not give us control over replication. Storage services have been introduced on gametest5 which should solve this problem. However, they are not perfect.

## Problem

Currently, on gametest5, there are two services: `ServerStorage`, the contents of which does not replicate, and which is present on all instances of ROBLOX, and `ReplicatedStorage`, which replicates in both directions (from server to client and from client to server). This does not allow us to prevent the client from replicating changes to the server, and the current names are misleading.

## Proposal

This proposal suggests:

* Renaming the current `ServerStorage` class to `PrivateStorage` and not changing its behavior.
* Making `ReplicatedStorage` not replicate from the client to the server and renaming it to `ProtectedStorage`.
* Adding a class called `PublicStorage` which replicates from the client to the server and from the server to the client.
