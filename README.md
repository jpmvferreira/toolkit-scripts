A set of scripts to manage Einstein Toolkit simulations.

Whenever I start a new project that uses the toolkit, this is what my folder strucuture looks like:
```
<project name>
├── bin/          # clone this repository here
├── exe/          # toolkit binary goes here
├── par/          # parfiles go here
├── simulations/  # output of the simulations, using simfactory conventions
└── (...)         # everything else
```

Brief description of each script:
- `run`: Runs a simulation with user specified parameters, either on localhost or via Slurm, from a new parfile or already existing simulation.
- `sync`: Selective (or total) sync the project folder with other machines.

To synchronize the project folder between hosts, `sync` assumes the existence of a file `host.json` in `bin/` with the format `host: folder`. Here's an example of what such a file could look like:
```
{
  "_comment": "file with known hosts and their corresponding project directories.",

  "some-cluster":    "/path/to/home/project-name",
  "another-cluster": "/mnt/path/to/project/project-name",
}
```

The file that are synchronized by default should be present in `include.txt`. You also have to add this file yourself. This gets processed by rsync, so everything that works with rsync works here as well (e.g.: wildcards). Here's how this file could look like:
```
out.log
*.par
carpet-grid-coordinates
carpet-grid-structure
BH_diagnostics.ah1.gp
```
