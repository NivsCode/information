### How does docker work?
Instead of the usual VMs inside a guest OS inside a Virtual Hardware powered by server's host OS, The containers run by leveraging the low level mechanics of the host OS. It provides most of the isolation of VMs at a fraction of cost and computing power.

### Why Docker?
Containers offer a logical packaging mechanism where apps can be abstracted from the env in which they actually run enabling easy deployment and consistency. This also includes increases control over resources and portability.

### Persisting a DB
We do this with mounting, creating a volume and attaching it to the directory where the data is stored, we can persist the data.

As mentioned, we are going to use a **named volume**. Think of a named volume as simply a bucket of data. Docker maintains the physical location on the disk and you only need to remember the name of the volume. Every time you use the volume, Docker will make sure the correct data is provided.

# Tags
#theory