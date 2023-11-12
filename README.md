# Satel Python Poetry Continous-Integration Document Generation

This centralized GitHub action runs tests on a python app using poetry

### Usage

```yml 
  poetry-redoc:
    timeout-minutes: 15
    runs-on: samba
    environment: ${{ inputs.environment }}
    env:
      PYTHON_VERSION: "<PYTHON_VERSION>"
    outputs:
      REDOC_LINKS: ${{ steps.links.outputs.REDOC_LINKS }}  
      COVERAGE_LINKS: ${{ steps.links.outputs.COVERAGE_LINKS }} 
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
          portal-url: "<PORTAL-URL>"
```
