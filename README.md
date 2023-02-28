# Grafana slack template

This is a grafana slack template that is a bit better than the default.

## Requirements

- Grafana +8 with new alerting

## Features

- Includes links to runbook, panel, dashboard, if present
- When multiple alerts trigger at once, extra alerts are listed with only the summary.

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

