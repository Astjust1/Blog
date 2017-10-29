Just a note. It seems like firebase doesn't completely update the site directory. So every time you change the way the site is structured, you need to disable hosting with
```firebase hosting:disable```.
Then redeploy using an empty commit.