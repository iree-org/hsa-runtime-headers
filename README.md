# hsa-runtime-headers

Headers for dynamically loading HSA extracted from the [ROCR-Runtime](https://github.com/ROCm/ROCR-Runtime) repository.

## Updating

* Copy the files from [runtime/hsa-runtime/inc](https://github.com/ROCm/ROCR-Runtime/tree/amd-staging/runtime/hsa-runtime/inc) to `include/hsa/`.
* Exclude `Brig.h`.
* Copy AQLProfile SDK headers from the ROCm `aqlprofile` project
  `src/core/include/aqlprofile-sdk/` to `include/aqlprofile-sdk/`.
* Use a configured `aqlprofile-sdk/version.h` from a matching ROCm build or
  release package; the source tree contains `version.h.in`.

## Local Patches

* `hsa_ven_amd_aqlprofile.h`: define
  `HSA_VEN_AMD_AQLPROFILE_LEGACY_PM4_PACKET_SIZE` as an anonymous enum instead
  of a file-scope `const unsigned`. In C, the upstream `const` definition has
  external linkage and produces duplicate symbols when the header is included
  by more than one translation unit.
