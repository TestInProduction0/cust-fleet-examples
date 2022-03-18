This is an older repository, originally meant to show off Fleet as a CD solution. I'm repurposing it to learn more about the KOTS platform. I decided to reduce complexity by pulling a simple stateless app that's original YAML can be found here: https://kubernetes.io/docs/tutorials/stateless-application/guestbook/

When starting out, I set out primarily with one goal in mind - to ingratiate myself in the actual KOTS app framework. I gravitated towards the preflight checks (preflight.yaml) immediately, as in previous discussions with software vendors I've worked with there's a common story of how difficult it is to create applications that were meant to conform to a specific standard and, when delivering said app on client sites, only in post-outage discussions was it revealed that the app was not running in a proper configuration.

The opportunity to configure my app in such a way that it gave a mix of recommendations, warnings, and generally document a hypothetical set of requirements is immediatley interesting to me as it allows for as tight or loose guardrails around the app as possible.

Having said all of that, my preflight.yaml is currently _not functioning_ in the App Manager UI, so it'd be nice to fix that.

Because of this, my application.yaml and config.yaml are more bare bones. The application.yaml really only creates some status informers of the relevant deployments and services to validate their health, and the config.yaml is not actually linked to the redis application at all and is really just me trying to throw things at the wall and see how they perform in the App Manager UI.

If I were to functionally own this application and move it forward, I would more than likely tear down much of the config.yaml to only parameters that would be relevant to a webserver, so more than likely just a cert/root CA variables. After that, I'd like to add a graph that visualizes the various deployments for liveness and readiness probe failures. If given time, visualizing traffic rates would be worth implementing as well.

In terms of what's missing, I have not implemented a support bundle or a troubleshooting.yaml, and they offer themselves as obvious 'next steps' as well. In my time spent learning the KOTS framework I believe the most interesting uses fall in the preflight.yaml, as it offers a very powerful toolset to guardrail licenses apps and in doing so reduce config drift at scale.

Yes, I'm committing directly to master. No, I'm not apologizing. I'd like my Dev dressed with Ops and small fries, please.