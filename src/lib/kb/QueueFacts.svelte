<script>
import { firstReceived, lastReceived, firstMerged, firstBatch, earlierReports, afterKnown } from '#lib/kb/incident-4471';
</script>
<p>Reports start on {firstReceived}. The first merge date is {firstMerged}: {firstBatch} reports were merged that day, including an earlier backlog; {earlierReports} reports had arrived before it. A merge spike measures desk processing, not the day the bug began.</p>
<p>Reports continue through {lastReceived}; {afterKnown} arrived after the incident page's 2026-09-30 review. “Known” and “fix queued” do not mean fixed. These are report and merge timestamps, not deployment or resolution evidence. Check subsequent intake and fix verification before changing status.</p>
