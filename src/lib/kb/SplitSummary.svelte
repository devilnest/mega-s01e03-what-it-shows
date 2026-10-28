<script lang="ts">
  import { raw, merged, groups, flagged, mismatches, firstReceived, lastReceived } from '#lib/kb/incident-4471';
  import tickets from '#lib/data/problem-tickets.json';
</script>
<p><strong>{merged.length} unique reports · {groups.length} classified causes</strong> in #4471, received {firstReceived} to {lastReceived}. The export has {raw.length} rows: {raw.length - merged.length} repeated rows are counted once by report ID.</p>
<div class="scroll"><table>
<thead><tr><th>Problem</th><th>Reports</th><th>Tenants</th><th>Received</th><th>Own ticket</th></tr></thead>
<tbody>{#each groups as g (g.cause)}<tr><td><code>{g.cause}</code></td><td>{g.reports.length}</td><td>{g.tenants}</td><td>{g.firstSeen} → {g.lastSeen}</td><td>{#if g.cause !== 'unplaced' && tickets[g.cause]}<a href={tickets[g.cause]}>GitHub issue</a>{:else}Prepared; awaiting publication{/if}</td></tr>{/each}</tbody>
</table></div>
<p>{mismatches} reports disagree with intake's browser-based tag. Use the tenant's locale and booking-form version with the report's channel; do not split by browser locale, intake tag, subject, or export row.</p>
<div class="scroll"><table><thead><tr><th>Classified cause</th><th>Tagged parser</th><th>Tagged hint</th></tr></thead><tbody>{#each groups as g (g.cause)}<tr><td>{g.cause}</td><td>{g.taggedAs.parser ?? 0}</td><td>{g.taggedAs.hint ?? 0}</td></tr>{/each}</tbody></table></div>
<p>{flagged.length} reports need symptom follow-up. Their IDs are {flagged.map(r=>r.id).join(', ')}. They remain in their classified group and are not counted again.</p>
<style>.scroll{overflow-x:auto}th,td{vertical-align:top}</style>
