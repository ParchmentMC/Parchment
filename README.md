Parchment Mappings
==================
This repository contains all the mappings and data related to making the parchment mappings.

## Contributing
1) Fork this project
2) Clone your fork
3) Create a directory `inputs` and create your staging change files in it.
4) Run the following gradle tasks in order:
   1) `createStagingFromInputs`
   2) `validateStagingData`
      A note on this task: It will validate your input and tell you if failed to follow any guidelines.
      Our CI system will also validate that your contributions follow these guidelines. **Any PR made that does not follow the guidelines will not be considered!**
   3) `promoteStagingToProduction`
5) Commit the changed files.
6) Push your commits to your fork.
7) Create a Pull Request to pull your changes from your Fork into this repository.
8) Await feedback and process your feedback that comes from the mapping management team.

## Compass & Staging files
Our mapping system makes use of [Compass](https://github.com/ParchmentMC/Compass).
This gradle based tool adds different tasks, but is also able to interpret different file formats to change the mappings in this repository.

The files needed to make changes need to be placed in the input directory, and are known as the `Staging Files`.
These files follow a specific format, which can be found [here](https://github.com/ParchmentMC/Compass/wiki/Simple-Input-Files).

## Documentation improvements
This is a relatively new project, and we need all the help we can get.
Since we currently are heavily focused on getting a release out, we need to excuse ourselves for the lack of documentation, it will improve over time.

## Getting help:
We provide public help in our Discord server, which you join using this [link](https://discord.gg/RDXVAV9h6F).

## Licensing
Parchment Mappings are released under the terms of the CC0 1.0 Universal (CC0 1.0). 