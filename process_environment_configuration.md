# Process Environment Configuration

Configuration via environment variables should always only happen at the
program's entrypoint. Environment variables should not be dealt with within the
depths of the code. Any program should operate on the basis of libraries which
provide certain modules or service implementations. These are then properly
configured at runtime by the means of dependency injection. Using environment
variables within imported libraries makes the daily business of maintenance and
extension nearly impossible and often requires huge refactoring efforts, because
once touched, everything falls apart and nobody knows where and why something is
actually broken.
