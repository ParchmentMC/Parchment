Thank you for deciding to contribute to the Parchment mappings! Whether you are writing some explanatory javadocs,
naming parameters, or even just correcting typos, we are glad to have you contribute.

## Setup

Setting up the repository for contributing is fairly simple.

### Prerequisites

- You have an account on [GitHub](https://github.com), and know how to use basic GitHub functions such as Pull Requests.
- You have basic knowledge of git (such as what commits are, what branches are), and using it (cloning a repository,
  pushing, pulling). This guide assumes you are using the terminal/command line for git operations. If you are using a
  GUI for git, please consult that application's manual/user guide on how to do these operations.

### Steps

1. **Fork the repository.** Forking the repository creates a copy of the repository (your _fork_) at your personal
   account, where you push your own commits to your branches.

1. **Clone your forked repository locally.** The repository directory can have any name, by default cloning will make a
   directory with the same name as the repository.

1. **Run Enigma through the `enigma` Gradle task.** [Enigma][enigma] is a mapping interface originally developed by
   Jeff Martin and now forked and maintained by the FabricMC team.

1. **Name parameters and create javadocs.**
	- Classes are listed at the top-left section of the interface. Double-click on a class to open it.
	- To name a parameter, either move the typing cursor to the parameter name and type the name then press
	  <kbd>Enter</kbd>, or right-click the parameter name and select `Rename` from the context menu.
	- To add javadocs to a class, field, method, or parameter, right-click the name and select `Edit Javadocs` from
	  the context menu.
	- To save your changes, press <kbd>Ctrl</kbd> + <kbd>S</kbd> or go to `File` > `Save`.
	- Be mindful of the [Mapping Standards][standards] while mapping.

1. _Recommended:_ Validate your data through the `validateData` Gradle task. This checks for errors in the mapped data,
   such as mapped/documented synthetic methods. This task is also ran by the CI on every Pull Request.
	- If there are validation errors, it is suggested to run the `sanitizeData` task to automatically sanitize the data
	  and remove potential causes of validation errors, such as synthetic methods.

1. **Open a Pull Request.** Pull Requests are reviewed and merged according to our [PR Review Process][review-and-merge].

[enigma]: https://github.com/FabricMC/enigma
[standards]: https://parchmentmc.org/docs/mappings.html
[review-and-merge]: https://parchmentmc.org/docs/review.html
