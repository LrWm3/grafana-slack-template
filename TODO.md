# Grafana Template ideas to explore

> Edit template so that 'from' & 'to' for cleared alerts pad with + 1m & -1m. 

Thought being it is useful to see slightly before and slightly after the alert flipped.

This might be possible by manipulating our {{ .StartsAt }} and {{ .EndsAt }} with go arthimatic tricks.

## Ideas I ultimately didn't like

> If the panel isn't assigned, the ref link points to the alert generator URL instead.

Decided these things serve too different a purpose to have them behind the same link. Also, want to encourage people to add panel links.

> All alerts listed / linked have the alert generator URL included.

I thought this would limit our maximum alerts per message too much. (would be like, max 16 cleared + firing at once I think, instead of 32, but I didn't recalculate this so I may be wrong).
