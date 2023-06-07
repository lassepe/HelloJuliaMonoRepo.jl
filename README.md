# Quick Start

- Create subprojects `A`, `B`, and `C` using `]generate A` etc. in a flat folder hierarchy.
- Activate the *parent* folder and issue `]dev ./A ./B ./C` dev them into a global environment
- Edit each `Project.toml` to include `manifest = "../Manifest.toml"`. This will make sure they all share the global resolver state; i.e. the global `Manifest.toml`
- Since everyone shares the global `Manifest.toml` with all subpackages deved,
  you can just add relative dev dependencies between pacdkages, e.g. `]dev A`
  from B, as you please. Only one global Manifest.toml will need to be
  maintained.

**Note:** When ever you `]update`, make sure that you have activated the outer
project. Otherwise, you may accidentally "delete" 
