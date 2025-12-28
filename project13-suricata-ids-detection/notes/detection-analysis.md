# Detection Analysis Notes

## Alert Summary
- Detection: clear-text credential keyword in HTTP POST body (`password=`)
- Data source: Suricata `fast.log`
- Type: policy violation (insecure credential handling)

## Why It Matters
Sending credentials over HTTP can expose sensitive data to interception. This detection simulates how a SOC can identify insecure application behavior.

## SOC Lesson Learned
A rule will not fire unless the traffic crosses the monitored interface. In this lab, Suricata needed to monitor the correct interface(s) to observe the victim’s outbound traffic.
