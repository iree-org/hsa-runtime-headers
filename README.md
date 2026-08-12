# hsa-runtime-headers

Headers for dynamically loading HSA and AQLProfile extracted from the
[ROCm rocm-systems](https://github.com/ROCm/rocm-systems) repository.

## Current Snapshot

The HSA and AQLProfile SDK headers are synchronized to rocm-systems commit
[`41e1945cebc29d93187537246f3ae5a5179373b2`](https://github.com/ROCm/rocm-systems/commit/41e1945cebc29d93187537246f3ae5a5179373b2).

## Updating

* Select one rocm-systems commit for the entire snapshot.
* Copy `projects/rocr-runtime/runtime/hsa-runtime/inc/` to `include/hsa/`,
  excluding `Brig.h`.
* Copy the public headers from
  `projects/aqlprofile/src/core/include/aqlprofile-sdk/` to
  `include/aqlprofile-sdk/`.
* Configure `aqlprofile-sdk/version.h` from `version.h.in` using the interface
  version and selected rocm-systems revision. Leave binary build metadata empty
  because this repository builds no AQLProfile library.
* Update the snapshot revision above in the same commit.

## Local Patches

* `hsa_ven_amd_aqlprofile.h`: define
  `HSA_VEN_AMD_AQLPROFILE_LEGACY_PM4_PACKET_SIZE` as an anonymous enum instead
  of a file-scope `const unsigned`. In C, the upstream `const` definition has
  external linkage and produces duplicate symbols when the header is included
  by more than one translation unit.
* Remove trailing whitespace from imported headers so snapshots satisfy the
  repository diff policy.
