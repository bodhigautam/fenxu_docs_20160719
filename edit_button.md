---
title: Edit Button
description: This topic describes the behavior of edit button by taking source into consideration
---

# Edit Button

Edit button is a component on docs page to let contributors or writers can quick access the source file. With this convenience, they could contribute to the documentation easily.

## Original Metadata And Logic For Edit Button
### Metadata
| Metadata Name | Value | Used by |
| ------------- | ----- | -------- |
| original_content_git_url | url of the file where documentation built and published from. | BI team: track conceptual article's publishing source file. |
| content_git_url | original_content_git_url's public mapping url. It is ususally used when parnter have public and private repository pair. So that non-Microsoft contributors can contribute on the public repository because they don't have access to the private repository. | N/A |
| original_ref_skeleton_git_url | Url of the file where documentation built and published from. Usually used in reference content or SDP type content. | BI team: track reference content publishing source file. |
| original_ref_skeleton_git_url | original_content_git_url's public mapping url. It is ususally used when parnter have public and private repository pair. So that non-Microsoft contributors can contribute on the public repository because they don't have access to the private repository. |

### Edit button logic


## New Requirement
The four metadata met previous requests. However, currently we have another requirement. It comes from windows, Rest teams. In their scenario, the relationship between repositories and docs site is like following shows.
![relationship between repos and docs site](images/edit_button/relationship_repo_docs.png)

1. There's a source repository which used for internal and outside writers to contribute. Trust that repository as source of truth.
2. CI processes the source rpeository, generate output and put that in the processing repository. Processing repository is an OPS provisoned repository.
3. OPS will publish the content from processing repository to docs site.

Under this process, OPS is only aware of processing repository. It doens't have any information of where source repository is. Besides, source repository and processing repository are not public and private likely repository. Thus, no way to let OPS system figure out the edit button value from those four files.
