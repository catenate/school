[[urbit app]] [[Hoon school]]

https://urbit.org/docs/development/environment

### Create a new desk

To create a new desk, you'll need to merge from an existing one, typically `%base`. In the dojo, run the following with your preferred desk name:

```hoon
|merge %school our %base
|mount %school
```

If you now mount it, you'll have `/mydesk` directory in your pier with all the files of the `%base` desk inside. You can then delete the contents, copy in your own files and `|commit` it.

Desks must contain all the `mark` files, libraries, etc, that they need. A `sys.kelvin` file is mandatory, and there are a few `mark` files necessary as well. In the next couple of sections we'll look at different ways to populate a new desk with the necessary files.

The desks in [[urbit/pkg]] ending in `-dev`, like `base-dev` and `garden-dev`, contain files for interfacing with those respective desks. If you're creating a new desk that has a tile and front-end, for example, you might like to use `base-dev` and `garden-dev` as a base. To create such a base, there's a `symbolic-merge.sh` script included in the directory. You can use it like so:

```shell
./symbolic-merge.sh base-dev school
./symbolic-merge.sh garden-dev school
```

Then, you can go into your pier:

```shell
cd /home/jdc/urbit/zod
```

Delete the contents of the new desk:

```shell
rm -r school/*
```

And then copy in the contents of the desk you created:

```shell
cp -rL ~/obsidian/flake/urbit/pkg/school/* school
```

Note you have to use `cp -rL` rather than just `cp -r` because the `symbolic-merge.sh` script creates symlinks, so the `L` flag is to resolve them and copy the actual files.

Now you can just add a `sys.kelvin` file:

```shell
echo '[%zuse 418]' > school/sys.kelvin
```

And you'll be able to mount the desk with 

```hoon
|commit %school
```

