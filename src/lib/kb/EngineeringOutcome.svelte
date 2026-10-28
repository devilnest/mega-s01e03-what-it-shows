<script>
import update from '#lib/data/engineering-update.json';
import tickets from '#lib/data/problem-tickets.json';
import { groups } from '#lib/kb/incident-4471';
</script>
<p>The desk marks source incident #{update.ticket} closed on {update.closedOn}. Its engineering update gives separate outcomes for the two causes:</p>
<div class="scroll"><table><thead><tr><th>Cause</th><th>Reports</th><th>Outcome</th><th>Engineering evidence</th><th>Ticket reason</th></tr></thead><tbody>{#each groups as g (g.cause)}{#if g.cause === 'parser' || g.cause === 'hint'}<tr><td><a href={tickets[g.cause]}>{g.cause}</a></td><td>{g.reports.length}</td><td><strong>{update[g.cause].outcome}</strong></td><td>{update[g.cause].evidence}</td><td><code>{update[g.cause].stateReason}</code></td></tr>{/if}{/each}</tbody></table></div>
<p>Source: the student's copy of the <a href={update.sourceUrl}>Challenge page's engineering update</a>, received {update.receivedOn}. The report counts remain the historical export counts. The desk's update supplies closure evidence; this KB review did not independently run the product's regression tests.</p>
<style>.scroll{overflow-x:auto}th,td{vertical-align:top}</style>
