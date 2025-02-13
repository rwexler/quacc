# FAQ

**Q: Which workflow management system should I use?**

A: Good question! Check out the [Workflow Engines Overview Guide](../user/basics/wflow_overview.md) for a comparison of several common options to see which might be best for you.

**Q: Why is quacc better than `InsertMyFavoriteCode`?**

A: Better is all in the eye of the beholder. If you are happy with the tools you are using, my goal is not to convince you to switch. That said, if you find that writing high-throughput computational workflows has a huge learning curve or simply takes too much time away from your science, then quacc may be for you.

**Q: Do you have any tips for writing new workflows?**

A: When developing new workflows, I strongly recommend writing an initial draft based on a low-cost ASE calculator like `EMT` or `LJ`, which will allow you to test on your local machine with fast turnaround. Also try to keep things modular. Trying to do too much in one function can make it difficult to debug.

**Q: How is quacc different than just using the [Atomic Simulation Environment (ASE)](https://wiki.fysik.dtu.dk/ase/)**

A: quacc is designed to supercharge ASE for the efficient design of high-throughput workflows. Quacc makes it possible to easily design complex ASE workflows that can be run on heterogeneous compute environments with modern workflow managers, such as [Covalent](https://github.com/AgnostiqHQ/covalent) and [Jobflow](https://github.com/materialsproject/jobflow). Quacc also makes it possible to combine ASE with the powerful [Materials Project](https://materialsproject.org/) software stack, such as [Custodian](https://github.com/materialsproject/custodian) for on-the-fly error handling. For the database enthusiasts, quacc is interoperable with [Maggma](https://github.com/materialsproject/maggma) to store calculation results in a readily queryable format like MongoDB.

**Q: How is quacc different than [Atomate2](https://github.com/materialsproject/atomate2)?**

A: Atomate2 is a fantastic code that can be used to run libraries of computational materials science workflows. Quacc was originally inspired by Atomate2 and can be thought of as a "sister code" to it. That said, there are several important differences.

- In Atomate2, workflows are built around the Materials Project software stack and can be cumbersome to interface with the [Atomic Simulation Environment (ASE)](https://wiki.fysik.dtu.dk/ase/). In contrast, quacc was built around ASE from the ground up while still making it possible to leverage much of the software underlying the Materials Project. Since quacc is built around ASE, it is also trivial to add new recipes based on any code that has an existing ASE Calculator even if it is not in quacc yet.

- Atomate2 is built around [Jobflow](https://github.com/materialsproject/jobflow). Quacc is largely workflow engine-agnostic and has out-of-the-box support for numerous workflow codes, including but not limited to Jobflow.

- Atomate2 is often used as a database-first approach to materials science workflows. Quacc is fully compatible with the use of databases but only emphasizes their use for experts, with the goal of reducing the barrier to getting started.

- Atomate2 is developed and supported by the [Materials Project](http://materialsproject.org/) team at Lawrence Berkeley National Laboratory. Quacc is developed and maintained by the [Rosen Research Group](https://rosen.cbe.princeton.edu/) at Princeton University.

Despite these differences, quacc and Atomate2 are largely interoperable! Feel free to [stitch together workflows](../user/advanced/atomate2.md) from both codes as you see fit using Jobflow!

**Q: I want to contribute a new recipe to quacc, but it will require additional dependencies. Is that a problem?**

A: Absolutely not a problem! Simply make your dependencies optional in the `pyproject.toml` file and use a `monty.dev.requires` decorator to ensure your recipes and tests only run if your necessary dependencies are installed. Refer to `quacc.recipes.tblite.core` and the `[tblite]` extras in the `pyproject.toml` file for an example.
