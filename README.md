# GPU for Scientific ML

Hands-on CUDA practice for scientific ML: thread indexing, memory hierarchy, kernel optimization, and custom GPU ops for PDE solvers.

## Learning path

| Module | Topics |
|--------|--------|
| `00_basics/` | Thread indexing, grids/blocks/warps, 1D/2D/3D launches |
| `01_memory/` | Global vs shared memory, coalescing, bandwidth |
| `02_optimization/` | Occupancy, profiling, streams |
| `03_numerics/` | Reductions, linear algebra, stencils |
| `04_sciml/` | Custom CUDA ops for PDE solvers |

## Requirements

- CMake ≥ 3.18
- CUDA toolkit (`nvcc` on `PATH`)
- Linux with an NVIDIA GPU, or a cloud GPU instance

macOS works for editing and notes, but CUDA must be built and run on a machine with a GPU (Lambda, Colab, RunPod, etc.).

## Build

```bash
cmake -B build -DCMAKE_CUDA_ARCHITECTURES=native
cmake --build build
```

Set an explicit SM target when cross-compiling or configuring without a local GPU:

```bash
cmake -B build -DCMAKE_CUDA_ARCHITECTURES=89   # Ada Lovelace (SM 8.9)
cmake --build build
```

## Adding an exercise

1. Add source under a module directory (e.g. `00_basics/hello/`).
2. Add a `CMakeLists.txt` in that directory with your target.
3. Wire it in from the root `CMakeLists.txt` via `add_subdirectory(...)`.
