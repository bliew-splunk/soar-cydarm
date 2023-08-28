# README
## Context
- SOAR app which integrates with Cydarm API
- https://support.cydarm.com/en/knowledge/api-documentation (requires login)

## Build
- A Github action called `Build SOAR App` has been setup which creates the SOAR app `.tgz` as an artifact.

## Structure of this repo
- `app/` contains all SOAR app files
- `package.sh` is used to create a `.tgz` SOAR app bundle
- `app/cydarm.json` is generated via `update_app_json.sh`, which runs the `gen_app_json` Python module

## Running `package.sh`
- requires the python package `pyclean` installed

## How to run tests (`test/`)
- Note that the tests in `test_cydarm_api.py` expect to hit a real Cydarm environment.
- Also some of the tests are hardcoded against my own Cydarm instance, so may fail in another env.
  - TODO: generalise any hardcoded tests OR use mocks instead of real requests.
- Python Requirements:
  - pytest
  - pytest-dotenv
- Create a `.env` file in repo root based on this template:
    ```
    CYDARM_BASE_URL=
    CYDARM_USERNAME=
    CYDARM_PASSWORD=
    ```
- Run `PYTHONPATH=. pytest -v test/` from repo root.