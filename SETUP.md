# Setting up the repository, without a terminal

Ten minutes in the browser. Nothing here needs a command line.

## 1. Create the repository

1. On github.com, click **+** then **New repository**.
2. Owner `coreydelizza-design`, name `stonemark-demo`.
3. Choose **Private**. Keep it private even though the demo itself will be public: the
   hosted page can be public while the source stays private, and that combination gives
   away nothing.
4. Add no README, no .gitignore and no licence — they are in this pack already, and
   GitHub's licence picker only offers open-source licences, which is the opposite of
   what this repo needs.
5. Click **Create repository**.

## 2. Upload this pack

1. On the new repository's page, click **uploading an existing file**.
2. Unzip the pack on your computer, then drag **all** of it in, folders included. If the
   browser refuses the folders, upload the root files first, then repeat for `.github`
   and for `docs/ip`, typing the folder path into the file-name box.
3. Commit message: `IP and governance files`. Commit straight to `main`.
4. Check that `.github/CODEOWNERS`, `.github/PULL_REQUEST_TEMPLATE.md`, `.gitignore` and
   the nine files in `docs/ip/` all arrived. Files beginning with a dot are easy for a
   browser to drop silently.

## 3. Turn on the protections

In **Settings**:

- **General → Features**: turn off Wikis and Projects. Fewer public surfaces to leak
  through.
- **Branches → Add branch ruleset**, targeting the default branch: require a pull request
  before merging, and turn on **Require review from Code Owners**. That makes
  `CODEOWNERS` mean something.
- **General → Pull Requests**: enable automatic deletion of merged branches, as on the
  platform repo.
- **Code security**: enable **Secret scanning** and **Push protection**. Push protection
  is the one that pays for itself: it blocks a credential before it reaches history,
  where removing it is much harder.

## 4. Close the four easy placeholders

Open `docs/ip/PLACEHOLDERS.md` and fill rows 1 to 4 — entity registration, address, and
the legal and security email addresses — by editing each file with the pencil icon. The
rest wait on counsel.

## 5. Then the build

Add `docs/packs/demo-buildout.md` and `docs/packs/demo-runner.md` the same way, and start
with Block A and step D0.

© 2026 Stonemark Infrastructure Assurance LLC. Confidential and proprietary.
