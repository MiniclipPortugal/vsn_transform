# vsn_transform

Erlang parse transform to add `vsn` attributes from e.g. Git info.

## Usage

Add the following to your `rebar.config` file:

    {deps, [
        {vsn_transform, "1.0.0",
            {git, "https://github.com/MiniclipPortugal/vsn_transform.git"}}
    ]}.

    {erl_opts, [
        {parse_transform, vsn_transform},
        {vsn_command, "git describe --tags"}
    ]}.

Obviously, you can change the command as needed. You might want to use `git
rev-parse --short HEAD`, for example:

        {vsn_command, "$BASE_DIR/git-vsn --friendly"}

... where `BASE_DIR` is an environment variable set in the top-level Makefile.

## Did it work?

You can check it with the following:

    vsn_transform:vsn(Mod).

where `Mod` is the module for which you want to obtain the `vsn_command`
output.

## License

Apache 2.0
