# Demo Binary Outputs

Pre-compiled demonstration binaries for the [Ghidra Optimized Vector Decompiler](https://github.com/mithro/ghidra-optimized-stdvector-decompiler).

This submodule stores test binaries compiled with different Windows C++ compilers to verify the plugin works correctly across compiler variations.

**Main Repository**: https://github.com/mithro/ghidra-optimized-stdvector-decompiler

## Compiler Matrix

| Compiler | Version | Build Date | Notes |
|----------|---------|------------|-------|
| clang-19 | 19.x.x  | 2025-11-09 | LLVM 19 with clang-cl MSVC compatibility |
| clang-20 | 20.x.x  | TBD        | LLVM 20 with clang-cl MSVC compatibility |
| msvc-14.44 | 14.44.35207 | TBD   | Native MSVC via Wine |

## Directory Structure

Each compiler has its own directory with O2 (optimized) and Od (debug) variants:
- `{compiler}/vector_basic_O2.exe` - Basic vector operations, optimized
- `{compiler}/vector_basic_O2.pdb` - Debug symbols for optimized build
- `{compiler}/vector_basic_Od.exe` - Basic vector operations, debug
- `{compiler}/vector_basic_Od.pdb` - Debug symbols for debug build
- `{compiler}/vector_extra_O2.exe` - Extended patterns, optimized
- `{compiler}/vector_extra_O2.pdb` - Debug symbols for optimized build
- `{compiler}/vector_extra_Od.exe` - Extended patterns, debug
- `{compiler}/vector_extra_Od.pdb` - Debug symbols for debug build

All binaries include PDB debug symbols for proper Ghidra analysis.

## Building New Compiler Variants

From main repository:

```bash
cd demo

# Build with specific compiler
make COMPILER=clang-20 all

# Commit to submodule
cd out
git add clang-20/
git commit -m "Add clang-20 binaries"
git push

# Update main repo reference
cd ../..
git add demo/out
git commit -m "Update demo binaries: add clang-20"
```
