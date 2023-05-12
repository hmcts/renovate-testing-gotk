# Minimal Reproduction of Renovate FluxCD/Fluxv2 Manager

This is a minimal reproduction repo for the issues seen and raised [here](https://github.com/renovatebot/renovate/discussions/22073)

## Current Behaviour

renovate.json fileMatch has been extended with the following regex to match all YAML files as per the [docs](https://docs.renovatebot.com/modules/manager/flux/#non-configured-filematch): 
````
"\\.yaml$"
````

Two gotk-components.yaml files have been created using the following command:
````
flux install --export > apps/flux-system/base/gotk-components.yaml
flux install --export > apps/flux-system/base/gotk-components2.yaml
````

Renovate Debug Logs shows match for both files by flux manager however after dependency extraction the flux manager fileCount & depCount are both listed as 1. 

Only gotk-components.yaml is shown on the dependency dashboard.

gotk-components2.yaml does not recieve dependency updates but gotk-components.yaml does despite the files having identical contents. This can be seen in the open PRs


## Expected Behaviour

Both gotk-components.yaml & gotk-compoents2.yaml should be included in dependency dashboard and recieve the same dependency updates.