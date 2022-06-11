# take arms against a sea of troubles

https://urbit.org/docs/hoon/hoon-school/caesar

_confer_ [[2022-06-10 04-39]]

## user

Rename this program.

	Edit ,s,arms,arms,g

Extract hoon files and copy it to [[fake ~zod]] desk.

```shell
lit 'lit=arms.md' 'file=arms.hoon'
cp arms.hoon /n/local/home/jdc/urbit/zod/tanote/gen/
```

Commit the file in the desk.

```hoon
|commit %tanote
```

## code

Enable a full stack trace in the event of an error.

	arms.hoon: !:

Create a gate that takes an atom.

	arms.hoon: |=  a=@

=< ([[tisgal]]) is the rune that evaluates its first child expression with respect to its second child expression as the subject. 

Compose two expressions, inverted.  `=<` is just `=>` ([[tisgar]]) backwards.

	arms.hoon: =<

Value returned by the generator.

	arms.hoon: =((double (plus-two a)) (plus-two-double a))

Arms that define the generator.

	arms.hoon: |%
	arms.hoon: ++  plus-two
	arms.hoon:   |=  a=@
	arms.hoon:   (add 2 a)
	arms.hoon: ++  double
	arms.hoon:   |=  a=@
	arms.hoon:   (mul 2 a)
	arms.hoon: ++  plus-two-double
	arms.hoon:   |=  a=@
	arms.hoon:   (double (plus-two a))
	arms.hoon: --

## test

Run the generator.

```hoon
+tanote!arms 11
```

Output of the generator.

```shell-session
52
```

