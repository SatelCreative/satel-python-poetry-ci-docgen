# Satel Python Poetry Continous-Integration-Doc-Generation

This centralized GitHub action runs tests on a python app using poetry

### Usage

```yml
name: Run tests
on: 
 <conditions-you-want-this-workflow-to-run-on>
  jobs:  
  code-validation:
    needs: [self-hosted-status]
    timeout-minutes: 15
    runs-on: ${{ contains(needs.self-hosted-status.outputs.runner-status, 'online') && 'self-hosted' || 'ubuntu-latest' }}
    environment: ${{ inputs.environment }}
    env:
      PYTHON_VERSION: "3.10"
    steps:
      - name: Check out repository
        uses: actions/checkout@v4.1.1

      - name: Poetry ci docgen
        uses: SatelCreative/satel-python-poetry-ci-docgen@1.0.0
        with:       
          app-name: ${{ inputs.app-name }}
          environment: ${{ inputs.environment }}
          work-dir: ${{ inputs.work-dir }}
          python-version: ${{ env.PYTHON_VERSION }} 
```