# Object Locking using S3 Object Lock

Object locking feature is built for addressing use cases where
Write Once Read Many (WORM) model is required. The feature will be built in line
with AWS specification, any extensions to the specification will be explicitly
documented. The feature implementation has the goal of meeting
SEC 17a-4 compliance.

## Requirements

* Bucket needs to have object lock flag set during bucket creation
* Versioning has to be enabled on the bucket
* Lock configuration can be written only on a bucket using PUT Object Lock
  Configuration api that has object lock flag set

PS: AWS specification does not have a way of setting object lock on existing
buckets cannot have object lock flag set through the api. To enable
object lock flag on an existing bucket, a migration needs to be performed
on the bucket using a tool. Objects that were created before the lock is set
are not protected by Object Locking

## What happens when an object is locked?

A lock can be set on an object version, it prevents deletes, overwrites on that
version until the lock expires. The lock however doesn't prevent creation of
delete markers or new versions on top of the locked version.
Object locking is also immune to Lifecycle actions i.e a lifecycle expiry rule
cannot delete an object version until the lock on the object expires.

## Controlling locking of an object

S3 provides a few ways thorough which locking configuration of an object can
be set

### Retention Modes

Both Governance and Compliance modes retain lock on an object until the set
retention period.

#### Governance mode

#### Compliance mode

### Retention Period

### Legal Hold
