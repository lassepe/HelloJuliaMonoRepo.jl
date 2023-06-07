:warning: This workflow requires Julia 1.9 or newer.

# Objective

This repository demonstrates the new `manifest = ...` field supported by the `Project.toml` in Julia 1.9 and above.
By setting this field, users can share a single `Manifest.toml` across multiple "subprojects".
This is handy in settings where where you want to develop packages jointly in a
single repository while still allowing each package have its own sub
environment (with individual dependencies).

**Note:** I'm not yet sure how to use this in the context of an `examples/` directory.

# Reproducing this Setup

- Create subprojects `A`, `B`, and `C` using `]generate A` etc. in a flat folder hierarchy.
- Activate the *parent* folder and issue `]dev ./A ./B ./C` dev them into a global environment
- Edit each `Project.toml` to include `manifest = "../Manifest.toml"`. This will make sure they all share the global resolver state; i.e. the global `Manifest.toml`
- Since everyone shares the global `Manifest.toml` with all subpackages deved,
  you can just add relative dev dependencies between pacdkages, e.g. `]dev A`
  from B, as you please. Only one global Manifest.toml will need to be
  maintained.

**Note:** When ever you `]update`, make sure that you have activated the outer
project. Otherwise, you may accidentally "delete" 
