# webcommit

Self-contained library to commit into GitHub.

Author: [Oleg Mihailik](mailto:mihailik@gmail.com) [@oyin.bo](https://bsky.app/profile/oyin.bo).

Using with no dependencies:

```javascript
const prepare = await webcommit({
  owner: 'oyin-bo',
  repo: 'webcommit',
  branch: 'test',
  auth: prompt('GITHUB AUTH')
});

await prepare.put(
  'test.txt',
  'No dependencies: ' + new Date()
);

const commit = await prepare.commit('Committing with no dependencies at all');
alert('Committed \n' + JSON.stringify(commit, null, 2));
```

With Octokit:

```javascript

const octokit = new Octokit({ auth: prompt('GITHUB AUTH') });
const prepare = await webcommit({
  owner: 'oyin-bo',
  repo: 'webcommit',
  branch: 'test',
  octokit // <-- here
});

await prepare.put(
  'test.txt',
  'Using Octokit: ' + new Date()
);

const commit = await prepare.commit('Using Octokit');

alert('Committed \n' + JSON.stringify(commit, null, 2));

```