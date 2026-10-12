# OpenMC in the browser (GitHub Codespaces)

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/bforget/openmc_cloud?quickstart=1)

## For students

1. Sign in to GitHub. If you're a student, apply for the free [GitHub Education](https://education.github.com/) benefit, which gives you more Codespaces hours.
2. Click the **Open in GitHub Codespaces** badge above, then **Create codespace**.
3. VS Code opens in your browser with `notebooks/00_check_setup.ipynb`. Click **Select Kernel → Python Environments → /openmc_venv/bin/python**, then **Run All**.
4. When you're done, **stop** the codespace (Codespaces menu, bottom-left → *Stop Current Codespace*). Your files are kept. Reopen it later from <https://github.com/codespaces>.

> Codespaces stop on their own after 30 minutes idle. Stopped codespaces that sit unused for a long time are deleted, so commit and push work you want to keep.

## What's inside

- `.devcontainer/Dockerfile` uses the official `openmc/openmc:v0.16.0` image, which already includes OpenMC, its Python API, and the NNDC HDF5 cross-section library (`OPENMC_CROSS_SECTIONS` is preset). It also adds Jupyter support.
- `.devcontainer/devcontainer.json` sets up a 2-core machine, the Python and Jupyter extensions, and the default interpreter.
- `notebooks/00_check_setup.ipynb` runs a UO2 pincell k-eff calculation as a smoke test.

---

## Instructor setup (one time)

1. **Create the repo.** On GitHub, create a new repo (e.g. `ne-openmc-course`), upload these files, and replace `OWNER/REPO` in the badge link above. Under *Settings → General*, tick **Template repository** so students (or GitHub Classroom) can copy it.
2. **Test it.** Click the badge yourself. The first build pulls a ~2 GB image and takes a few minutes. The creation log should end with `OpenMC 0.16.0 | data: /root/nndc_hdf5/cross_sections.xml`.
3. **Turn on prebuilds (makes student startup fast).** *Settings → Codespaces → Set up prebuild*: branch `main`, configuration `.devcontainer/devcontainer.json`, trigger **On configuration change**, and region(s) near you (US East). Prebuild storage is billed to the repo owner, so put the repo in an org covered by the Education benefit (step 4), or keep prebuilds to one region.
4. **Pick a way to distribute it:**
   - **Simple:** share the badge link. Each student's codespace uses *their own* free monthly quota (more with GitHub Education).
   - **GitHub Classroom:** as a verified teacher, create a Classroom org (upgraded to GitHub Team for free via GitHub Education) and enable Codespaces *from Classroom*. Then use this repo as the assignment template. Usage bills to the classroom's education allowance instead of the students. See [Using Codespaces with GitHub Classroom](https://docs.github.com/en/education/manage-coursework-with-github-classroom/integrate-github-classroom-with-an-ide/using-github-codespaces-with-github-classroom).
5. **Add course material** as notebooks in `notebooks/`. Pushing changes to `.devcontainer/` triggers a new prebuild automatically.

### Customizing

- **Different nuclear data (e.g. ENDF/B-VIII.0):** uncomment the block at the bottom of the Dockerfile. It makes the image larger and prebuilds slower.
- **Bigger problems:** raise `hostRequirements.cpus` to 4 in `devcontainer.json`. Hours are counted in *core*-hours, so a 4-core machine uses quota twice as fast.
- **Upgrading OpenMC:** change the image tag (e.g. `v0.16.1`) between semesters, not mid-course.
