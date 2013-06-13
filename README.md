craftsmanship
=============

A collection of documentation on project contribution guidelines and general adopted practices. This project itself should conform to these guidelines.

#Project Contribution
##Branching Model
All projects will follow the [gitflow branching model](http://nvie.com/posts/a-successful-git-branching-model/), using [gitflow](https://github.com/nvie/gitflow).

##Project Creation
1. Clone the repository.
2. Initialize git flow: `git flow init -d`

#Development
Features must be named in the format: `feature/feature-name` this can be achieved without gitflow, but using gitflow makes it that much easier.

1. Create a new feature: `git flow feature start new-feature`
2. Do your work, commit as needed.
3. Publish the feature: `git flow feature publish new-feature`
4. Submit a pull request.
5. When good, merge or: `git flow feature finish new-feature`

Completing a feature will merge it into the `develop` branch which is used for integration purposes.

The `master` branch is used for production code.

#Testing
Test all the things. More to come...

#Releasing
Release names should follow the [semantic versioning](http://semver.org/) protocol:

1. Start a release: `git flow release start 1.0.1`
2. Commit version bump, final tweaks and changelog updates.
2. Finish a release: `git flow release finish 1.0.1`
3. Deploy `master` branch.

#Conforming
To mark a project as conforming with these guidelines in your own documentation simply plop this little snippet in your `README.md` file:

    ##Contribution Guidelines
    This project conforms to the [neverstopbuilding/craftsmanship](https://github.com/neverstopbuilding/craftsmanship) guidlines. Please see that repository for details on project administration.
