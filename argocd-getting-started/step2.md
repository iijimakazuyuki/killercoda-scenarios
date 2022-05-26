Take a declarative approach in this course though Argo CD can be set up via UI.

Before setting up Argo CD, create your own Git repository in GitHub.
If you don't have your GitHub account, follow the GitHub Docs: [Getting started with your GitHub account Part 1: Configuring your GitHub account](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account#part-1-configuring-your-github-account)

Fork the sample repository `https://github.com/iijimakazuyuki/katacoda-argocd-sample` or create like the sample repository and note the following:

- Only `podinfo-application.yaml` file is required.
- `README.md` and `LICENSE` are unnecessary files.
- Though Argo CD can access private repositories using given credentials, set your repository public for the sake of simplicity.

Next, set auto sync to your Git repository and deploy a sample application.
