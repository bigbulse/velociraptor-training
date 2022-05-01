---
description: Create an artifact to detect "Update.bat"
---

# 📄 Assignment 1

Updated versions of the Pysa ransomware use an "Update.bat" file that deletes attack information.

### Task 1:

Create a file in <mark style="color:blue;">`C:\windows\temp`</mark> named "Update.bat"

### Task 2:

Using this starter format, create an <mark style="color:green;">Artifact</mark> to <mark style="color:green;">Hunt</mark> for the "update.bat" file. &#x20;

{% content-ref url="../../using-velociraptor/artifacts.md" %}
[artifacts.md](../../using-velociraptor/artifacts.md)
{% endcontent-ref %}

```yaml
name: Pysa.SelfDeletion.Finder
description: |
   This artifact searches for the Pysa ransomware "update.bat" file.

type: CLIENT

parameters:
   - name: FirstParameter
     default: Default Value of first parameter

sources:
  - name: MySource
    precondition:
      SELECT OS From info() where OS = 'windows'

    query: |
      SELECT * FROM info()
      LIMIT 10

```

#### Hint:&#x20;

Try looking at <mark style="color:green;">Artifacts</mark> used in the Pysa Hunt for reference.
