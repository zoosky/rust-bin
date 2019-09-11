<div align="center">
  🗑️
</div>
<h1 align="center">
  rust bin
</h1>

<div align="center">
   A recipe for <a href="https://www.rust-lang.org/">Rust</a> bins built, tested, and published with <a href="https://help.github.com/en/categories/automating-your-workflow-with-github-actions">GitHub Actions</a>.
</div>

<br />

> **⚠️ Note:** To use GitHub Actions, you must have access to the [GitHub Actions](https://github.com/features/actions) feature. GitHub Actions are currently only available in public beta. You can [apply for the GitHub Actions beta here](https://github.com/features/actions/signup/).

## How to use this repo

This repository is meant to use as a template for new Rust projects intended to produce
a binary for users to run.

### cargo generate

This repository works well with the [`cargo generate`](https://github.com/ashleygwilliams/cargo-generate) plugin.

You can install `cargo generate` with the following

```sh
$ cargo install cargo-generate \
	--features vendored-openssl
```

Then generate a new rust bin project with run the following providing a name `--name` option with the name of the binary
you want to generate

```sh
$ cargo generate \
	--git https://github.com/softprops/rust-bin.git
	--name my-awesome-rust-bin
```

> **⚠️ Note:** Be sure to edit the `package.name` in the resulting project with the name of the binary you wish to produce


[Create a new git repository](https://help.github.com/en/articles/create-a-repo) on GitHub.com

In your generated project, complete the repository setup process and push to GitHub

```sh
git init
git commit -m "init to winit"
git remote add origin git@github.com:{you}/{my-awesome-rust-bin}.git
git push -u origin master
```

Assumming you have already [applied for the GitHub Actions beta here](https://github.com/features/actions/signup/) and received
your invite you should find GitHub already going to work for you on your first `push` by visiting

```
https://github.com/{you}/{my-awesome-rust-bin}/actions
```

You'll notice this workflow ends with a publish step but does not actually publishing anything yet.

The reason why is that you typically only want to publish a release by [tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging) a release.

Let's try that.

```sh
git tag -a v0.1.0 -m "initial release"
git push origin v0.1.0
```

Visit `https://github.com/{you}/{my-awesome-rust-bin}/actions` once more and you should find another workflow run has started. This time the workflow will end with a publish step that will create a new GitHub release named after the tag.

You can find your GitHub releases here.

```
https://github.com/{you}/{my-awesome-rust-bin}/releases
```

You should find 3 assets attached to your GitHub release. One for `linux`, one for `OSX`, and one for `windows`. Download the one for the type of operating system you are using by clicking the link.

Unpack the asset locally and run it.

Congradulations. You've just shipped your first release! Now you can share your awesome Rust binaries with all your friends.