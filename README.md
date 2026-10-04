    # Timeflow Card for NSLS-II schedule
    This is a work in progress, I'll try to clean things up soon.
    THIS INSTALLS AS A HOME ASSISTANT BLUEPRINT and it's based off of [Timeflowcard](https://github.com/Rishi8078/TimeFlow-Card).

    REQUIRED SETUP: Configure rest_command.nsls_ii_fetch_current_status with

    url https://www.bnl.gov/nsls2/schedule/fetch-current-status.php, method GET,

    timeout 30, and restart Home Assistant. Create two Text helpers (maximum

    length at least 64) and two Date and/or time helpers with BOTH date and time.

    Select all four below. Run the resulting automation once to initialize it.


    Store each published transition plus a fixed 30-second grace period in the

    existing next-transition helper. Refresh at that stored time, at Home

    Assistant startup, and once daily at 03:00:30 in your HA timezone. The

    displayed countdown also includes the grace period; notification dates

    quote the published transition without it. No extra helper, variable, or

    input is needed. Unchanged refreshes preserve the countdown start.


    Failed requests or invalid responses preserve all previous helper values

    and mark the trace failed. This is the operating SCHEDULE, not live beam

    availability. Brookhaven dates are interpreted in US Eastern time (modern

    US DST rules), independently of your HA timezone.


    OPTIONAL NOTIFICATIONS: Enable status-change notifications and select one

    or more notify entities. This same automation sends a message only when a

    previously known current status changes after a successful fetch. Initial

    setup, unchanged refreshes, and next-status/date revisions are silent.

    A change discovered after HA was offline sends one catch-up notification.


    Distribution: copy this file into blueprints/automation/nsls_ii/ and follow

    the accompanying README and TimeFlow card example. A blueprint cannot

    create the required REST command, helpers, or dashboard card itself.

    Add source_url under blueprint after publishing this file at a real URL.