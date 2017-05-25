# RedmineAPI
Python class for easy redmine access
### Assigning an issue back to the author
```python
issue_info = self.redmine.get_issue_data(issue_id)
self.redmine.update_issue(issue_id, assign_to_id=issue_info['issue']['author']['id'])
```
