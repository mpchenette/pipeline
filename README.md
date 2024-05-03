## Best Practices
- It is recommended that you:
  - include a display name on your YAML pipeline steps to increase visibility and understanding of what is happening
  - not use Classic Build or Classic Release pipelines as they do not scale easily


## To Do
- add logic to infrastructure pre-processing to run pwsh if .ps1 or bash if .sh
- add enum for file extension for each infrastructure language

### Example Usage
First, create a Service Connection to this GitHub repository.

Next, in a git repo, create a YAML file with the following contents:

``` yaml
resources:
  repositories:
    - repository: pipeline
      type: github
      endpoint: <your_github_service_connection>
      name: mpchenette/pipeline

parameters:
  - name: environment
    values: [dev, test, prod]
    default: dev

extends:
  template: main.yml@pipeline
  parameters:
    environment: ${{ parameters.environment }}
```

replacing `<your_github_service_connection>` with the name of the GitHub service connection you created.