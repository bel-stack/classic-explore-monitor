# Google Trends Classic Explore monitor - one-file GitHub Actions setup

This is a ready-to-use GitHub Actions workflow. **It has not been installed or enabled in your GitHub account yet.** It checks the exact Classic Explore URL you supplied, twice a day at 9:17 AM and 5:17 PM New York time (EST/EDT).

## Easiest setup without installing software

1. In GitHub, create a new repository called `classic-explore-monitor`. A **public repo** uses free standard GitHub-hosted runner minutes; a private repo draws on your account's included Actions minutes. Do not put private data in a public repository.
2. In the new repo, choose **Add file > Create new file**.
3. Enter `.github/workflows/check-classic-explore.yml` as the file name.
4. Open that same path in this downloaded folder, copy the entire YAML into the GitHub editor, then **Commit changes**.
5. Go to the repository's **Actions** tab > **Check Google Trends Classic Explore** > **Run workflow**. Verify that a check completes.
6. To see alerts, go to **Watch > All Activity** for that repo and make sure GitHub email notifications are enabled. A new issue titled "Google Trends Classic Explore may have been retired" is created and assigned to the repository owner only if the new UI appears on **both** independent browser attempts.

## What happens

- **AVAILABLE:** Classic-specific chart widgets exist, and the Interest over time chart or data response appears. No alert.
- **LIKELY_RETIRED:** On two independent browser sessions during a single run, the new UI appears and old Classic widgets are absent. A GitHub Issue is created and assigned to the repository owner. The issue title says *may have been retired* because this is not definitive proof.
- **INCONCLUSIVE:** Google shows a CAPTCHA, blocks the bot, times out, or returns an unexpected layout. No retirement alert. Review the run logs or screenshots manually. If all runs are inconclusive, GitHub cloud monitoring isn't a reliable approach for this page.

Screenshots and results are attached to the workflow run under **Artifacts** for seven days. The URL is specifically `https://trends.google.com/trends/explore?q=coconut&date=now%201-d&geo=PH&legacy&hl=en`.

GitHub schedule times may be delayed, and public repo scheduled workflows can be disabled after 60 days with no repository activity. Google may block automated access to Explore, and its robots.txt has been reported to restrict `explore` automated crawling. Use a low frequency, respect any access restrictions, and don't treat automated failure as definitive retirement.

## Cost

There are no recurring Codex calls. Standard GitHub-hosted Actions runners are free for public repos. Private repositories have a monthly included allowance under GitHub's current plans, and excess usage can be billable. The browser installation takes minutes and might be a poor fit if your repo is subject to tight quotas.

## How to stop

Open the repo's **Actions** tab > select the workflow > **Disable workflow**, or remove `.github/workflows/check-classic-explore.yml`.
