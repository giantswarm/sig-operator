# Fine Grained Operators

In SIG operator we want to drive a clear separation of concerns and keep our
microservices properly cut. An operator should only deal with its own business
domain. An operator might want to run multiple controllers and manage different
resources within a system. One good indicator is the lifecycle and various
concerns about setup and teardown of a system's resources.
