# Grafana slack template

This is a grafana slack template that is a bit better than the default.

## Requirements

- Grafana +8 with new alerting

## Features

- Includes links to runbook, panel, dashboard, if present
- When multiple alerts trigger at once, extra alerts are listed with only the summary.
- Each alert line item in the group includes a link to the related panel, if present
- Links to dashboard and panel with the correct time, showing 10 minutes surrounding the alert trigger
- Links to dashboard and panel with the labels provided by the alert, allowing for the automatic population of variables for dashboard and alert links if they match.
- A backlink to view the alert is created.

## Usage

In `Grafana > Alerts > Contact Points > Message Templates`

Add copy and paste the contents of `./grafana-slack-body.gohtml` into a named template called `slack_body_prod`.

Add copy and paste the contents of `./grafana-slack-header.gohtml` into a named template called `slack_header_prod`.

In your slack notification policy:

Add the following for `Title` 

```
{{ template "slack_header_prod" . }}
```

Add the following for `Text Body`

```
{{ template "slackBody" . }}
```

It will now use this custom template for slack instead of the default one.

## Including variables in your alerts

To include variables in your alerts, you can extract labels during your queries and then use them like so:

Example Summary field:
```
[Critical] [{{ $labels.environment }}] Host[{{ $labels.Host_IP }}] appears to be offline!
```
