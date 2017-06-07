# RedmineAPI
Python class for easy Redmine access

## Creating a new redmine interface instance
Use this to access redmine
- url: Redmine url in this format - http://redmine.biodiversity.agr.gc.ca/
- api_key: Your redmine api key - You can find your API key on your account page ( /my/account ) when logged in, on the right-hand pane of the default layout.
- wait_between_retry_attempts: How many seconds to wait between retry attempts when accessing Redmine
```python
redmine = RedmineInterface('http://redmine.biodiversity.agr.gc.ca/', 'foo')
```

## upload_file
For attaching a file to a Redmine issue
- filepath: Path to the file you want to upload
- issue_id: ID of the Redmine issue you want to upload the file to
- content_type: The content type of the file you are uploading, please check on [this webpage](http://www.freeformatter.com/mime-types-list.html)
- file_name_once_uploaded: The filename once it's on Redmine
- additional_notes: Notes to upload the file with
- status_change: Number from 2 - 5, 2 is in progress, 3 is resolved, 4 is feedback, 5 is closed.
        
#### Example
```python
redmine = RedmineInterface(...)
redmine.upload_file("/home/file.zip", 123, "application/zip")
```
## get_new_issues
Get x newest open issues
- project: in the url of your issues page eg. http://redmine.biodiversity.agr.gc.a/projects/*cfia*/issues has the project cfia
- num_issues: how many issues to retrieve (default 25)
- returns dictionary of issues

#### Example
```python
redmine = RedmineInterface(...)
issues = get_new_issues('cfia')
issue_1_subject = issues['issues'][0]['subject']
```

## get_issue_data
Get data for a specific issue
- issue_id: Redmine issue id
- returns dictionary of the issue.

#### Example
```python
redmine = RedmineInterface(...)
issue = get_issue_data(1234)
issue_1_descr = issue['issue']['description']
```

## update_issue
Update a Redmine issue
- issue_id: Redmine ID of the issue you want to update
- notes: What you want to write in the notes
- status_change: Number from 2 - 5, 2 is in progress, 3 is resolved, 4 is feedback, 5 is closed.
- assign_to_id: ID number of the user you want to assign the issue to

#### Example
```python
redmine = RedmineInterface(...)
redmine.update_issue(1234, notes="Hello world!", status_change=4)
```

## assign_to_author
Update a Redmine issue
- issue_id: Redmine ID of the issue you want to update
- notes: What you want to write in the notes
- status_change: Number from 2 - 5, 2 is in progress, 3 is resolved, 4 is feedback, 5 is closed.

#### Example
```python
redmine = RedmineInterface(...)
redmine.assign_to_author(1234, notes="Hello world!", status_change=4)
```