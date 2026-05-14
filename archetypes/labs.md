+++
title = '{{ replace .Name "-" " " | title }}'
date = {{ .Date }}
tags = ["lab"]
type = 'lab'
difficulty = 'medium'
vms = [{ name = "example-vm", ip = "10.0.0.5"}]
summary = 'Short summary of the target and objective.'
resources = []
+++

<!--more-->
# {{ replace .Name "-" " " | title }}

Write an executive summary, goals, steps, commands, screenshots, and lessons learned.
