[[urbit app]] [[Hoon school]]

https://dev.tlon.io/

## create desk files

The optional `desk.ship` file specifies the original publisher of this desk. Since we merged this from `%garden` it's currently set to `~mister-dister-dozzod-dozzod`. Let's change this to our fake ship `~zod`. In practice you'll set this to the ID you want to be seen as the publisher (likely your own Urbit ID). Currently there is no verification that makes sure publishers are honest about this, but eventually there will be.

```bash
echo "~ponhec-picwen" > school/desk.ship
```

The final file we need to edit is `desk.docket-0`.  #now

```hoon
:~  title+'School'
    info+'Hoon school work'
    color+0x81.88c9
    version+[0 0 1]
    website+'https://github.com/catenate/school'
    license+'MIT'
    base+'school'
    glob-ames+[~zod 0v0]
    image+'https://media.urbit.org/docs/userspace/dist/wut.svg'
==
```

Commit and install our changes.

```bash
|commit %school
|install our %school
```

Open a browser and navigate to [localhost:80](http://localhost:80) .  To get the login code ([[access key]]), enter `+code` into the [[dojo]] prompt for your ship.  For [[fake ~zod]]s, the code is always `lidlut-tabwed-pillex-ridrup`.  You'll see our tile, but it says installing with a spinner due to the missing glob.

