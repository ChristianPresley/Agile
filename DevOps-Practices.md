# Platform-centric DevOps Practices

---

# Table of contents

  - [Communities of Practice](#communities-of-practice)
  - [Team Autonomy](#team-autonomy)
  - [Coaching and Organizational Support](#coaching-and-organizational-support)
  - [Continuous Integration (CI)](#continuous-integration-ci)

## Communities of Practice

When adopting the DevOps culture, it is crucial to establish communities of practice. Using a model similiar to [open-source software (OSS)](https://en.wikipedia.org/wiki/Open-source_software), central, or platform-based teams are setup to manage content and collaborate with developers, analysts, and other contributors from external teams. By doing so, the business is able to take advantage of lessons learned during the development of a work product and leverage those assets across the company, saving time and resources, while minimizing service degradation and outages.

Sometimes two platform teams are created to work in tandem, with the idea that they work as a check and balance for each other, ensuring a playful competitive nature that inspires and empowers innovation, and helps prevent the teams from becoming complacent or falling back into learned habits. Typically they are the "platform" team and the "center of excellence" team who share the same product leadership.

## Team Autonomy

Individual and team autonomy is the cornerstone of highly productive and qualitative product delivery teams. Autonomous teams are synomous with self-organizing, self-managing, or empowered teams.

One of the earliest references to autonomous teams comes from a research book published in 1981 on English coal miners, and describes it as: "Teams of 10 to 15 cross-trained individuals guided by the corporate vision, motivated by peer-pressure, and taking on the responsibilities of their former supervisors."

Autonomy refers to the team being provided freedom by leadership and management to complete their work, and for the individual to assert that autonomy in their everyday work to accomplish the goals and vision of the business with a sense of shared-purpose.

Cross-fertilization is the concept of the team being composed of individuals with different specializations, behaviors and thinking so that during the course of these individuals interaction they can improve their understanding of each other's perspective, which generally leads to better or higher quality outcomes.

Self-transendence is the concept of individuals on a team to self-evaluate their performance, set better goals, and design better solutions to achieve their personal and shared goals.

Contrary to the terms described above, this does not mean leadership or management becomes irrelevant. In fact, they become far more crucial to the team success, and take on more of a coaching role rather than a command & control approach. For most intents and purposes, individual success becomes shared team success, and the focus should be on creating work that is interdependent within the autonomous team rather than not. This focus will drive individual engagement, accountability, and higher quality outcomes.

Accordingly, autonomous teams can flounder if not proactively supported by leadership, and providing them a high level of autonomoy could reduce the teams overall effectiveness in delivering value to the business. The actual performance of the team relies heavily on management providing organizational context to the work being performed, essentially creating a feeling of shared-purpose or shared-goals.

References: [Autonomous agile teams: challenges and future directions for research](https://dl.acm.org/doi/10.1145/3234152.3234182)

## Coaching and Organizational Support

Leadership and management must provide organizational context, otherwise the individuals will struggle to come up with the shared-goal, and when they do complete work, they do not get the sense of accomplishment they otherwise would have.

Not providing adequate organizational context can lead to situations where the individual becomes too dependent on other teams to provide the context for them, which will prevent them from completing their work. Because of this, trust between individual and leader starts to erode, as from the individuals perspective, they are asked to do increasingly difficult work without any idea as to the goal being achieved. If you have experienced individuals pushing blame or providing constraints to why their work cannot be completed, this is an indicator that not enough context is being provided when the work was assigned.

During the process of defining context and giving work meaning, it can become apparent that architectural design or strategy becomes cumbersome and leads to unnecessary feedback loops or dependencies, where most of the time is spent planning what will be delivered rather than actually delivering work.

Coaching is the act of inspiring others to come up with solutions and pinpointing the challenge that individual is encountering. Those individuals are the closest to the work being completed, and so their knowledge on the subject is critical in coming up with a solution to the problem. Stoking their thought process to view the problem from different points of view is critical in unblocking work.

Lastly, informal rules or norms become a problem when regulating team behavior. Typically, a working agreement that all individuals and leadership agree to is required to prevent the team from going off in directions that are not desirable. An example [Working Agreement](Working-Agreement.md) can be found in this repository.

## Continuous Integration (CI)

Continuous integration is the process of building and/or testing code each and every time someone makes changes to the `main` branch of source control management (SCM), such as `Git` or `Subversion` (SVN). The `main` branch should be considered the `production` branch and should be able to deploy services at any given time.

Protecting the `main` branch from undesirable behavior is crucial to the integrity of the product and the ability to deploy services to production. One of the primary methods for protecting the `main` branch is to require `Pull Requests`, which is synonomous with code review or peer review. The Pull Request process allows automated tests to run and return the results so that time is not wasted during the review of changes. It also allows you to prevent the individual who created the changes from circumventing the process of committing changes to the `main` branch without peer-review.

The `Pull Request` also allows you to make direct comments on changes that have been made, and to provide clarity or context to code that is not immediately understandable. This process of commenting in `Pull Requests` has the side benefit of allowing individuals who are not experts in a certain area to learn from their peers.

The most widely adopted branching strategy is the [Trunk Based Development](https://trunkbaseddevelopment.com/) approach.

```
A source-control branching model, where developers collaborate on code in a single branch
called ‘trunk’ *, resist any pressure to create other long-lived development branches by
employing documented techniques. They therefore avoid merge hell, do not break the build,
and live happily ever after.

* main or master, in Git nomenclature
```

![Trunk-Based Development at Scale](trunk-development-at-scale.png)

As the graphic demonstrates, all individual contributors create a branch based on their assigned work item(s) when they start the work, and it's now considered `Work In Progress` (WIP). 

The most common nomenclature for these individual branches ties it together with the Agile work items that are assigned.

Features: `feat/description`

Bug: `bug/description`

Hotfix: `hf/description`

You can have additional identifiers, such as the work item number, but these can quickly diverge from the work being performed, such as if the work item splits into multiple, the work item is cut during Agile planning, or the work is not delivered in a given Agile iteration.

It is not recommended to create a branch with an identifier for the individual performing the work. The primary reasons are because the individual could be reassigned to a different task, they could take time-off or sick-leave during the work, or even someone else contributing to the work item. Instead of relying on the branch name to identify the individual(s) performing the work, use references to the user account that made the commit.

Note: the user account making changes is identified through the `Pull Request` process as well.

### Testing

Testing early and often during development is necessary to maintaining and delivering high-quality products. The concept of "Shift left" requires, among other things, unit testing to ensure desired outcomes and that defects are identified early in the process instead of during peer-review or `Product Owner` acceptance, or worst case scenario in production.

It's a heavily researched rule that in software development or infrastructure development the earlier in the process that you find an error, the easier, quicker, and cheaper it is to fix. The later in the process that you catch an error, the harder and more complicated it is to fix.


#### Unit Testing

The design of a `Unit Test` is to narrowly target the work that is being completed to minimize the potential for defects later in the release cycle. If there any any external dependencies, such as libraries or packages that must be built, external connections to databases or other live applications, that is not considered a `Unit Test` and could cause automation to fail with a false positive.

A proper unit test should also take a few seconds to run at most, and ideally be run in milliseconds. If unit testing takes longer than that, it indicates there are problems with the code being written and refactoring may be required. Alternatively, it could indicate that the test is actually an integration or external test, and should not be included in the `Unit Test`.

Typically if a `Unit Test` requires an external dependency, such as a connection to a database, then a mocking framework should be used in place of that dependency. For example, if it's a SQL database connection, then something like SQL in-memory can be utilized on the build agent that's running the `Unit Test` which would act as if it was the external SQL database.

A couple examples of a `Unit Test`:
- If you were designing a method to do simple math addition, you would take a known input such as 1 + 1 and call the method, and if the method returns anything other than 2 it should fail.
- 

#### Linting

Linting is the process of syntax and styles checking. When dealing with Infrastructure-as-Code (IaC) such as ARM Templates, Azure Bicep, Terraform, CloudFormation and others, it is crucial to perform linting prior to deployment of the infrastructure. Failing to do this could result in undesirable effects, such as changing one resource but not others, implementing a dependency that fails to deploy, or even removing quotas or limitations that could lead to overspending on resources.

Styles are important for readability and maintainability of code. Problems occur when a different style is used among developers working in the same code base. By having standards for code styles, it makes it easier to collaborate and understand what your peers are doing without having to meet with them to understand their code. The process of linting and style checking removes barriers to deployment of services and applications, significantly reducing both time to deploy and catch defects introduced during development.

The process of linting helps with the concept of Don't Repeat Yourself (DRY) in that it will be more apparent when code is repeated. Establishing patterns is directly valuable to the business and allows code to be shared across organizations instead of just within the team.

Linting can also ensure consistenty with parameters and arguments, and this is especially useful when using CI/CD tooling that relies heavily on runtime parameters to change the behavior of deployments, or when applications use Operating System Environment Variables.

### Work Item Acceptance

The `Product Owner` is the gatekeeper for accepting or rejecting work items, usually in the form of `User Stories`.

If the work item delivers work product (artifacts) outside of source control, the artifact should be uploaded to a permanent location and instructions on retrieving the artifact or a hyperlink should be applied to the work item. If a suitable permanent location is not available, the artifact should be attached to the work item delivering the artifact.

If the work item delivers artifacts that are inside of source control, the team member must initiate a `Pull Request` to the `main` branch. The `Product Owner` should be notified that they have a pending request to review the `Pull Request` and either accept or reject it based on peer-review feedback of the `Pull Request`.

In most cases, the peer-review can be done by any other individual on the team, including the `Product Owner`. If subject matter expertise is required, it is recommended to work with the individual that initiated the `Pull Request` to determine if it delivers on the acceptance criteria of the work item, and sometimes a demonstration of the work is necessary to satisfy the requirements. If the initiator is not available, than another subject matter expert should be identified and consulted to determine if the `Pull Request` delivers on the work item acceptance criteria.

The individual(s) reviewing the `Pull Request` should use a Definition of Done [(example)](Definition-of-Done.md) checklist to ensure that any gaps are identified before the `Pull Request` is accepted. If minor changes are required, it is not necessary to reject the `Pull Request` and instead the initiator should make the changes, and notify the reviewers that the work has been completed. If major changes are required, the `Pull Request` should be rejected and a new one must be initiated once the work has been completed.

### Release Management

The responsibility of tagging a release is that of the `Product Owner`. During the Agile iteration closing ceremonies, the `Product Owner` figuratively or literally declares the `main` branch complete for the iteration, and if production release is necessary, will proceed to tag the `commit` with the iterations release number. Tagging of the branch is usually delegated to a team member familiar with `git` and can appropriately select the `commit` to apply the necessary release tag. The release tag can be the same as the iteration number, or if using iteration schemes that do not reflect `release` tags, the `release` tag for an iteration should be determined at the start of the Agile iteration.

Generally, the `main` branch is the same as the `release`, however, sometimes it is necessary to `cherry-pick` specific commits for production release, usually in the event of needing a `hotfix` that is necessary to resolve a problem or defect. It is up to the `Product Owner` to determine exactly what would need to be `cherry-picked` and moved into the production release.

This release tag will be used as the basis for versioning any artifacts that are produced by the CI process(es), and any subsequent Continuous Delivery (CD) process(es) will utilize packages that are created from the `commit` that is tagged with the release version.

Conceptually, in the event of losing the artifacts or needing to reproduce the chain of events, this allows the product to be released back into production as if the artifacts were not affected by an event. On occasion, this can also be used to recreate to artifacts during regression testing if a bug or defect is introduced into production, and to validate that the CI process is consistent.

