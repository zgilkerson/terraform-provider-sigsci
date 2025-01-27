### Example Usage

```hcl-terraform
resource "sigsci_site_alert" "test" {
  site_short_name    = sigsci_site.my-site.short_name
  tag_name           = sigsci_site_signal_tag.test_tag.id
  long_name          = "test_alert"
  interval           = 10
  threshold          = 12
  enabled            = true
  action             = "info"
  skip_notifications = true
}
```

### Argument Reference
 - `site_short_name` - (Required) Identifying name of the site
 - `tag_name` - (Required) The name of the tag whose occurrences the alert is watching. Must match an existing tag
 - `long_name` -  A human readable description of the alert. Must be between 3 and 25 characters.
 - `interval` - (Required) The number of minutes of past traffic to examine. Must be 1, 10 or 60.
 - `threshold` - (Required) The number of occurrences of the tag in the interval needed to trigger the alert.
 - `action` -  A flag that describes what happens when the alert is triggered. 'info' creates an incident in the dashboard. 'flagged' creates an incident and blocks traffic for 24 hours.
 - `skip_notifications` -  A boolean flag to send notifications
 - `enabled`: A flag that describes whether the site alert should be enabled after its creation or not.

### Import
You can import corp lists with the generic site import formula

### Attributes Reference
In addition to all arguments, the following fields are also available
 - `id` - the identifier of the resource
 
Example:
```shell script
terraform import sigsci_site_alert.test site_short_name:id
```
