# Bug AimBot

This action helps developers find bug incuding commits using a tool known as Locus <br />
Locus: LOcates bugs from software Change hUnkS <br />
Locus source code: https://github.com/justinwm/Locus/

## Usage

* Add this action to your workflows
* Create a new issue with a title and body that contain meaningful information about the bug
* The action will do the rest of the work for you and present the commits that are most likely to blame for the bug in a comment underneath the issue

```yaml
name: Bug Aimbot

on:
  issues:
    type:
      - opened
        
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: vcu-swim-lab/bug-aimbot-action@v1.0.1
```

## How it works

This action uses the text from the title and body of the issue and sends that and some other important information to our Locus tool.
Token corpora are created using the issue title and body as a bug report. Locus takes this bug report and all the changes committed before this bug was reported as the input. Each hunk is indexed as an independent document to be ranked based on the vector space model. The output of Locus is a ranked list of commits that most likely caused the bug.

## Limitations

* If there is a quotation mark used in either the title or the body of the issue, it must have an accompanying quotation mark or the action will not work.
* The action relies on information from the title and body of issues, therefore it must be used as shown above.

## Contributors

* Justin Ruffin
* Bharath Mahendran
* Dhruv Sapra  
* Rohan Repala
