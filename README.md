<div align="center"><h1>Actions Auto Reviews From Selected Branches</h1></div>

This action is a automatic reviews from selected branches.

## Configuration with With

The following settings must be passed as environment variables as shown in the
example.

| Key            | Value                                                                | Suggested Type | Required | Default                   |
| -------------- | -------------------------------------------------------------------- | -------------- | -------- | ------------------------- |
| `GITHUB_TOKEN` | Personal github token. **recommend use GITHUN_TOKEN**                | `secret env`   | **Yes**  | N/A                       |
| `EVENT_TYPE`   | Type of event will have `APPROVED`, `COMMENT` and `REQUEST_CHANGES`. | `env`          | No       | `APPROVE`                 |
| `BRANCHES`     | Select the branch that you want to use.                              | `env`          | No       | `release/*`               |
| `MESSAGE`      | Can add comment at event select.                                     | `env`          | No       | `Thank you for approved.` |

## Example usage

```yml
name: Auto reviews release
on: pull_request
jobs:
  reviews:
    runs-on: ubuntu-latest
    steps:
      - name: Auto approve
        uses: ./
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN}}
          EVENT_TYPE: 'APPROVE'
          BRANCHES: 'release/*'
          MESSAGE: 'Nice approve from github bot.'
```
