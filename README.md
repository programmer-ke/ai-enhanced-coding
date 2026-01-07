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

Next create a task list. In my case, I like using the [vertical
feature slicing][vert] approach, a kind of evolutionary approach to
feature development.

[vert]: https://old.reddit.com/r/agile/comments/1btxpzd/vertical_slicing_the_single_most_impactful/

A prompt like the following can be used (modify as needed):

```
Based on the generated MVP spec, create a detailed step-by-step plan to
build this project.

Inspired by functional core, imperative shell pattern, we shall
separate the core business logic from the shell that handles
interactions with the external world: APIs, DBs etc

The business logic should be pure and side effect free without any
external dependencies and decoupled from infrastructure concerns
which makes it easier to write unit tests for.

The outer imperative shell shall reside in the app layer.

We'll use the vertical feature slicing approach for breaking down the
PRD into a thin end-to-end tasks that cut across the the
core business logic and the app layers.

With thin vertical feature slicing, each task (slice) builds onto the
previous one in an evolutionary manner.

Create a todo list representing the tasks in order of implementation

# VERY IMPORTANT
- Use markdown
- Each coding task should represent a thin vertical feature slice with
  an end to end implementation across the business logic and app layers
  (functional core and imperative shell) with applicable automated tests
  where necessary.
- We should be able to change each task's status from todo -> in
  progress -> done
- Each task should have a number id
```

Save the output of this into a `todo.md` file, tweaking where necessary.

# References

https://github.com/automata/aicodeguide

https://old.reddit.com/r/agile/comments/1btxpzd/vertical_slicing_the_single_most_impactful/
