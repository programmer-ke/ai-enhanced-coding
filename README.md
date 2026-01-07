# AI-enhanced Project Planning and Development

The initial motivation was this [AI coding guide][aicode]. In my case
I wanted to de-emphasize the vibe-coding aspect and document what I
find generally works for me with AI collaboration.

[aicode]: https://github.com/automata/aicodeguide

As such, this is expected to be an evolving guide as I learn more and
add/remove things.

## AI prompts to assist a project initiation and planning phase

### Build an MVP Spec

Start with the following prompt:

```
You are brainstorming with a senior software engineer with the goal
of producing an MVP Spec.

# VERY IMPORTANT

- Ask one question at a time
- Each question should be based on previous answers
- Go deeper on every important detail required

# IDEA

I'm building an MVP of the following:

<Describe the idea in a few paragraphs here>
```

Answer questions for a few minutes with as much detail as you feel is
necessary, until done or you decide is enough.


If necessary, use a prompt like the following to use the context of
the previous conversation to create an MVP spec.

```
Compile those findings into an MVP spec. Use markdown format.
It should include information like:

- Project overview
- Core requirements
- Core features
- Core components
- App/user flow
```

Copy the result to a `docs/specs.md` and review and edit the spec as
you see fit.

## Create a todo list

Next create a todo list with the user story format, starting from the
most basic end-to-end functionality.

In my case, I like using the [vertical
feature slicing][vert] approach, a kind of evolutionary approach to
feature development.

[vert]: https://web.archive.org/web/20260107094342/https://old.reddit.com/r/agile/comments/1btxpzd/vertical_slicing_the_single_most_impactful/

A prompt like the following can be used (modify as needed):

```
Based on the generated MVP spec, create a todo list in the form of user
stories to build this project.

Use the user story structure:

“As a [persona], I [want to], [so that].”

Using the evolutionary vertical feature slicing approach, each
slice should be a task that delivers a tiny bit of value to the
end user end-to-end and builds on previous tasks.

Intermediate shortcuts can be taken where necessary
e.g. hardcoding some values, or using a flat-file for storage
if subsequent tasks will replace them with production ready
equivalents.

Create a todo list representing the tasks in order of implementation

# VERY IMPORTANT
- Use markdown
- Each task should represent a thin vertical feature slice 
  that delivers some value to an end user or administrator
- We should be able to change each task's status from todo -> in
  progress -> done
- Each task should have a number id
```

Save the output of this into a `todo.md` file, making changes where
necessary. As you work through the tasks you may have to change some
of them or even the overall approach based on acquired feedback or
updated information.

## Architecture

Depending on the complexity, I'll use either the [Functional Core
Imperative Shell][fcis] pattern, or [Domain Driven Design][ddd].

[fcis]: https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell
[ddd]: https://www.cosmicpython.com/

Where applicable, I can break down each task using FCIS with a prompt
like:

```
I'd like to approach task x using the functional core imperative
shell pattern.

The functional core will express the domain or business logic
in a way that is easily testable via TDD with deterministic
inputs and outputs.

This will be surrounded by the imperative shell that takes
care of real world I/O like filesystem, database and
network access.

Suggest an approach if possible and if it doesn't add too
much indirection to affect readability.
```

# References

https://github.com/automata/aicodeguide

https://web.archive.org/web/20260107094342/https://old.reddit.com/r/agile/comments/1btxpzd/vertical_slicing_the_single_most_impactful/

https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell

https://www.cosmicpython.com/
