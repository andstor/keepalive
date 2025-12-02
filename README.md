# keepalive

A GitHub workflow to keep Hugging Face Spaces alive by pinging them daily.

## Usage

1. Fork or clone this repository
2. Edit `.github/workflows/keepalive-hf-spaces.yml`
3. Replace the example space with your Hugging Face spaces in the format `username/spacename`:

```yaml
strategy:
  matrix:
    space:
      - your-username/your-space-name
      - another-username/another-space
```

4. The workflow will automatically run once a day at 00:00 UTC
5. You can also manually trigger it from the Actions tab

**Note:** The workflow includes `example-user/example-space` by default. Replace this with your actual spaces.

## How it works

The workflow:
- Runs once a day using a cron schedule
- Uses a matrix strategy to ping multiple spaces in parallel
- Converts `username/spacename` to the URL format: `https://spacename-username.hf.space/health`
- Uses curl with a 10-second timeout to ping each space
- Continues even if some spaces fail to respond

## Example

If you add `andstor/my-cool-app` to the matrix, the workflow will ping:
```
https://my-cool-app-andstor.hf.space/health
```