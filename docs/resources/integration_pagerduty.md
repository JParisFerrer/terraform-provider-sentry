---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "sentry_integration_pagerduty Resource - terraform-provider-sentry"
subcategory: ""
description: |-
  Manage a PagerDuty service integration.
---

# sentry_integration_pagerduty (Resource)

Manage a PagerDuty service integration.

## Example Usage

```terraform
# Retrieve the PagerDuty organization integration
data "sentry_organization_integration" "pagerduty" {
  organization = "my-organization"

  provider_key = "pagerduty"
  name         = "my-pagerduty-organization"
}

# Associate a PagerDuty service and integration key with a Sentry PagerDuty integration
resource "sentry_integration_pagerduty" "test" {
  organization   = "my-organization"
  integration_id = data.sentry_organization_integration.pagerduty.id

  service         = "my-pagerduty-service"
  integration_key = "my-pagerduty-integration-key"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `integration_id` (String) The ID of the PagerDuty integration. Source from the URL `https://<organization>.sentry.io/settings/integrations/pagerduty/<integration-id>/` or use the `sentry_organization_integration` data source.
- `integration_key` (String) The integration key of the PagerDuty service.
- `organization` (String) The slug of the organization the resource belongs to.
- `service` (String) The name of the PagerDuty service.

### Read-Only

- `id` (String) The ID of this resource.

## Import

Import is supported using the following syntax:

```shell
# import using the organization slug from the URL:
# https://sentry.io/api/0/organizations/[org-slug]/integrations/
# [integration-id] is the top-level `id` of the PagerDuty organization integration
# [service-id] is the `id` of the service_table record to import under the configData property
terraform import sentry_integration_pagerduty.default org-slug/integration-id/service-id
```