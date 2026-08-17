Every git commit format should have these:

- **Type**: Use lowercase (e.g., feat, fix).

- **Scope (optional):** Specify affected area (e.g., ui, api).

- **Description**: Short (50-72 chars), imperative mood (e.g., "add login button").

- **Issue Hash (optional):** Reference issue tracker ID (e.g., #123) to link the commit to a specific issue in tools like GitHub, GitLab, or Jira. Place at the end of the description.

Format:

```git
<type> ([optional scope]): <description> [ #<issue-hash>]
```

Example:

```git
feat(ui): add login button #123
```

#### Common Types:

- **feat:** New feature (e.g., **`feat(ui): add smiley face painter #123`**).

- **fix:** Bug fix (e.g., **`fix: correct button alignment #456`**).

- **docs:** Documentation changes (e.g., **`docs: update README #789`**).

- **style:** Code formatting (e.g., **`style: apply prettier #101`**).

- **refactor:** Code restructuring (e.g., **`refactor: simplify auth logic #202`**).

- **test:** Add/modify tests (e.g., **`test: add login tests #303`**).

- **chore:** Maintenance tasks (e.g., **`chore: update dependencies #404`**).

- **perf:** Performance improvements (e.g., **perf: optimize queries #505**).

- **ci:** CI/CD changes (e.g., **ci: add linting step #606**).

- **build:** Build system changes (e.g., **`build: update Webpack #707`**).

- **revert:** Revert a commit (e.g., **`revert: undo feat(ui) #808`**).

#### Breaking Changes:

To indicate this change might break something then add **!** after type/scope. Example:

```git
feat (api)! : change endpoint #909
```


#### Optional Body:

For more in-depth description if needed. Add details below the first line, separated by a blank line

```git
feat(ui): add login button #123

- Add styled button component
- Implement click handler
- Resolves #123
```

#### Issue Hash Changes:

Include issue-number (e.g., #123) to reference an issue. Used for tracking purposes in issue trackers (e.g., GitHub auto-links #123 to issue 123).
Multiple issues: List as #123 #124 or in the body. Example:

``` git
fix(ui): resolve button overlap

- Closes #456
```
