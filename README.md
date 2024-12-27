# rubensapto.github.io

rubensapto.github.io is used by GitHub Actions to deploy rubensapto.cosa.site
files. This project drives the live "rubensapto.como" web site.

## DNS Configuration

1. In order to forward  `rubensapto.com` to your GitHub Page User
   Site `rubensapto.github.io` the following DNS CNAME record needs to be
   updated in both the GitHub User Site repository and in `GoDaddy.com`.
2. Sign in to the [GoDaddy.com](https://www.godaddy.com/) using the
   account `rubens_gomes` that is administrating the domain `rubensapto.com`.
3. Configure 4 (four) DNS A records with each A record pointing to the IP
   address of GitHub Pages:

    ```text
    A  @  185.199.108.153  600 seconds
    A  @  185.199.109.153  1 Hour
    A  @  185.199.110.153  1 Hour
    A  @  185.199.111.153  1 Hour
    ```

4. Create a DNS CNAME record for `www` that points `@`

    ```text
    cname  www  @  1 Hour
    ```

5. To verify that DNS records are working ensure that one of the GitHub IP
   addresses above are displayed from command:

    ```bash
    nslookup rubensapto.com
    ```

6. Finally to ensure the site uses HTTPS
   then [Enforce HTTPS](https://docs.github.com/en/github/working-with-github-pages/securing-your-github-pages-site-with-https#enforcing-https-for-your-github-pages-site)
   by checking "Enforce HTTPS" in the repository settings.

## GitHub Free User Site Pages

### Create Public GitHub Repositories

- `rubensapto.github.io`

- It is assumed that the DNS configuration was done for the site domain (eg.,
  rubensapto.com).
- See previous document section for DNS settings.


1. Login to your GitHub account.
2. Create a public repository named `[username].github.io` (e.g.,
   rubensapto.github.io).

    1. Select "Add a README File".
    2. Under "Description (optional)" enter a generic message (e.g., Rubens Apto
       Personal Site).
    3. For more information refer
       to [Creating a repository for your site](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site#creating-a-repository-for-your-site).

3. Select Settings under the newly created Git repository.
    1. Go to the "Pages" Configuration section.
    2. Click on Build and deployment Source drop-down menus
    3. Select "Deploy from a branch"
    4. Under the "Custom domain" section enter and save the registered domain
       name of your site (e.g., rubensapto.com).
    5. Ensure GitHub Pages site is currently built from the main branch ("
       branch: main") in the "/ (root)" folder. 
   6. Ensure "Enforce HTTPS" is selected. 
   7. For more information, refer
       to [Configuring subdomain](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain)

4. Ensure you have a file called "CNAME" in the public folder of your website
   with the domain name in it. For example, CNAME for rubensapto.com contains:

```
rubensapto.com
```

4. Run a `deploy.sh` build.
5. Once build is deployed to the "/" folder of the "main" branch you may access
   your User Site as `https://[username].github.io/`
   or `https://<actual-domain>/`.  (e.g., <https://rubensapto.com/>).

## Stylint

The stylint settings are configred in the project ".stylelintrc.json" file. For
further stylint settings information refer
to [stylint](https://github.com/bjankord/stylelint-config-sass-guidelines).

To run stylint in the scss code:

```bash
npm run css-lint
```


