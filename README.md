# rustlings

My local copy of the [rustlings](https://rustlings.rust-lang.org/) exercises.

## Minimum Requirements

* [mise](https://mise.jdx.dev/getting-started.html)
* [taskfile](https://taskfile.dev/docs/installation)

## Recommended Requirements

* [run](https://run.esubalew.dev/)

## Setup

```bash
# runtimes
mise install

# deps
task install
```

## Quickstart

```bash
λ rustlings
```

<!-- markdownlint-disable MD034 -->

> Is this your first time? Don't worry, Rustlings is made for beginners!
> We are going to teach you a lot of things about Rust, but before we can
> get started, here are some notes about how Rustlings operates:
>
> 1. The central concept behind Rustlings is that you solve exercises. These
>    exercises usually contain some compiler or logic errors which cause the
>    exercise to fail compilation or testing. It's your job to find all errors
>    and fix them!
> 2. Make sure to have your editor open in the `rustlings/` directory. Rustlings
>    will show you the path of the current exercise under the progress bar. Open
>    the exercise file in your editor, fix errors and save the file. Rustlings
>    will automatically detect the file change and rerun the exercise. If all
>    errors are fixed, Rustlings will ask you to move on to the next exercise.
> 3. If you're stuck on an exercise, enter `h` to show a hint.
> 4. If an exercise doesn't make sense to you, feel free to open an issue on
>    GitHub! (https://github.com/rust-lang/rustlings). We look at every issue, and
>    sometimes, other learners do too so you can help each other out!
>
> Press ENTER to continue

## Use `run` REPL

```bash
λ run exercises/00_intro/intro1.rs  # can specify rust explicitly via `run rs ...`
```
