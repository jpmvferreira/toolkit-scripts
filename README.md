This repository contains a set of scripts to manage Einstein Toolkit installations and simulations.

Whenever I start a new project that uses the toolkit, this is what my folder structure looks like:
```
<project name>
├── bin/          # clone this repository here
├── exe/          # toolkit binary goes here
├── par/          # parfiles go here
├── simulations/  # output of the simulations, using simfactory conventions
└── (...)         # everything else
```

The toolkit uses the default installation scheme.

Brief description of each script:
- `run`: Runs a simulation with user specified parameters. Supports localhost or Slurm.
- `build`: Builds the toolkit.
- `sync`: Syncs the folder with other machines.

To synchronize the folder between hosts, `sync` assumes the existence of a file `host.json` with the format `host: folder`. Here's an example of what such a file could look like:
```
{
  "_comment": "file with known hosts and their corresponding project directories.",

  "some-cluster":    "/path/to/home/project-name",
  "another-cluster": "/mnt/path/to/project/project-name",
}
```

For more information, each script has an help dialog.
