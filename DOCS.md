# Writing vulnerability reports

This file defines how final vulnerability reports for this project should be
written. The intended reader is a triager or product security engineer who
does not know the laboratory or the investigation history.

## General standard

Write the final submission in English. Use direct sentences, active voice and
ordinary technical language. State what was observed before explaining how it
was found. A reader should understand the affected feature, the required
conditions and the measured impact from the opening paragraph.

Use the first person when it identifies an action the researcher performed or
an observation the researcher personally confirmed. Direct phrases such as
`I configured the connection` and `I observed the restart` make evidence
ownership explicit. Do not force the first person into implementation details,
root-cause statements or general product behavior. Those claims should remain
objective and supported by the evidence.

Prefer short clauses and full stops over sentences built from several
comma-separated ideas. Keep commas where they help grammar or meaning. The goal
is natural technical prose, not the mechanical removal of every comma. A
useful revision test is to split a sentence when it contains more than one
distinct action, condition or result.

Avoid inflated claims, promotional language and generic filler. Do not call an
issue critical, exploitable or remotely reachable unless the evidence proves
that exact claim. Separate facts, reasonable inferences and untested
possibilities. Reverse engineering can explain the root cause, but observable
product behavior must carry the report.

A report should not be an uninterrupted wall of prose. Make it didactic by
combining short explanations with concrete technical material. Use code blocks
for exact requests, payload structures, commands and short trace excerpts. Use
tables for baseline comparisons, affected versions, process measurements and
recovery timing. Use a compact diagram when it clarifies network routing,
component boundaries, parser flow or the attacker position. Add annotated
screenshots when a configuration or visible result cannot be conveyed more
clearly as text.

Every visual element must answer a specific question. Introduce it in one
sentence, give it a descriptive title or caption, then explain the conclusion
that can be drawn from it. Keep raw output out of diagrams and avoid decorative
graphics. A reader should still understand the report if an image fails to
load, so preserve decisive values and observations in the surrounding text.

Prefer affirmative, evidence-led wording. Describe what the test used, what it
triggered, when it stopped and what was restored. Do not fill the report with
lists of services that were unaffected, impacts that were not found or attack
classes that were never part of the claim. Add a limitation only when it
changes reachability, reproducibility, severity or version attribution.

Translate technical measurements into their concrete effect where the evidence
is presented. Explain what a protected user sees, what a client application
receives, whether the destination receives the connection and what restores
normal operation. Keep that explanation next to the baseline and triggered
results. Do not create an extra section merely to label the impact when it fits
naturally into an existing evidence section. A reader should be able to move
directly from the measured worker or parser behavior to its effect on the
product and its users.

Avoid self-certifying qualifiers and obvious formulas. Do not announce that a
procedure is safe, a report is professional or an explanation is clear. Make
those qualities visible through precise facts, useful structure and measured
results. Use short factual section titles. Remove any sentence that adds no
evidence, instruction or necessary scope.

Capture the general editorial lesson rather than preserving the exact wording
of a correction made to one report. A narrow example can guide revision, but it
should not become a rigid phrase that every future report repeats.

Use calendar dates for provenance and relative durations for measured impact.
Reserve absolute clock times for attached logs or events that must be
correlated across machines. Process identifiers, hashes and offsets should
remain when they establish identity, worker distribution or code-path evidence.

Do not use em dashes or semicolons. Prefer a full stop, a comma or a short new
sentence. Remove phrases such as "it is important to note", repeated
conclusions and mechanical transitions. Read the report aloud once before
submission. It should sound like an engineer explaining a defect to another
engineer.

## Markdown conventions

Use one unnumbered level-one heading for the report title. Use unnumbered
level-two headings for the main sections. Do not prefix section headings with
numbers such as `1. Overview` or `2. Reproduction`. Numbering is reserved for
ordered procedures such as reproduction steps.

Follow this pattern:

```markdown
# Specific vulnerability title and demonstrated impact

**Submission channel:** Bug bounty platform / Product Security

**Report date:** 4 September 2026

**Product tested:** Exact product, version, build and model

**Affected component:** `binary-or-library` and affected parser or service

**Suggested priority:** P3 with a short factual qualification

**Status:** Confirmed result on the tested runtime

> One short paragraph that states the defect, trigger and measured impact.

## Overview

Opening explanation.

## Tested environment

Environment table.

## Reproduction

1. First reproducible action.

2. Second reproducible action.

## Runtime evidence

Measured results.

## Root cause

Technical explanation connected to runtime evidence.
```

Keep headings short, factual and written in sentence case. Add a blank line
after every heading and between paragraphs. Use level-three headings only when
a long section contains genuinely distinct subjects. Do not create a heading
for a single sentence or use headings to restate conclusions already visible
in the preceding evidence.

Use bold labels for the compact report metadata below the title. Place the
opening technical summary in a blockquote. Keep it to one paragraph and include
the trigger, affected component and strongest measured result.

Use fenced blocks tagged `text` for protocol layouts and arithmetic. A fenced
block tagged `text` or `yaml` remains preformatted text and does not become a
rendered diagram. Use the appropriate language tag such as `bash` or `python`
for commands and code. Use inline code for paths, process names, functions,
protocol fields, command-line arguments and exact values that are easier to
distinguish from prose.

For a real diagram in a Bugcrowd report, export a restrained PNG with readable
labels and a plain background. Upload it as an attachment, use Bugcrowd's copy
as Markdown action, then paste the generated embed at the relevant point in the
report. Keep embedded images below 2 MB for reliable inline display. Do not use
a local path in the final report. Do not rely on Mermaid unless the destination
renderer explicitly supports it. Keep a short textual explanation around the
image so the evidence remains understandable if it does not load.

Follow the technical diagram rules below. Create diagrams with an editable
vector or diagram tool such as Figma, diagrams.net or Graphviz. Do not use
generative image tools for architecture, protocol or code-path diagrams.

Use Markdown tables for exact comparisons and repeated measurements. Keep one
kind of measurement per column and include units in the heading or values.
Introduce the table with a sentence and explain its conclusion immediately
after it when the implication is not self-evident.

Use numbered lists for actions that must be performed in order. Use bullet
lists for expected results, prerequisites or attachments when order does not
matter. Keep ordinary explanations in paragraphs. Do not turn every sentence
into a bullet point.

Wrap prose at a consistent readable width, preferably around 80 characters,
without breaking inline code unnecessarily. Do not use HTML layout, manual
line-break escapes or decorative separators. The report must remain readable
as plain Markdown and after being pasted into the Bugcrowd description field.

## Technical diagrams

A technical diagram is part of the evidence. It must clarify a route, sequence,
state transition or causal relationship that takes longer to understand in
prose. Do not add one only to make the report appear complete. Give the reader
enough information to understand the figure without knowing the laboratory.

Name every actor by role and network position. Replace vague labels such as
"protected client" with a concrete description such as "internal client behind
the firewall" and state whether it is a browser, application, server or test
host. Identify the security component by product function, not only by a binary
name.

Label protocol transitions precisely. State the network direction, protocol
version, connection phase and exact message type. "TLS 1.3" alone is not an
adequate connector label. Prefer a description such as "Outbound TCP connection
and TLS 1.3 ClientHello" or "TLS 1.3 Certificate message returned during the
handshake". Make it clear whether the trigger is an HTTP request, a TLS record,
a handshake message, a certificate field or application data. State when no
HTTP request is required if that fact changes reachability or user interaction.

Show the complete causal chain from input to visible effect. Include exact field
sizes, cursor values, integer conversions and boundary conditions when they are
central to the defect. Use ordinary language for the operation and monospace
text for arithmetic, protocol fields, offsets and function names. A reader
should see why the parser repeats, which resource is consumed and why an
unrelated connection fails.

Distinguish observed behavior from inference inside the figure just as in the
report. Do not turn an expected consequence into an unconditional statement.
For example, if socket closure was not tested directly, describe the verified
code behavior such as the absence of further socket reads or connection-state
checks. Keep longer qualifications in the surrounding prose when adding them
would overload the figure.

Use a plain white canvas. Avoid off-white decorative backgrounds, gradients,
shadows, glows, glass effects, textures and three-dimensional elements. These
effects add no technical information and can make a diagram look like a generic
presentation or generated interface.

Do not build every part as a rounded card. Repeated large corner radii, equal
floating panels, badges and cards inside cards create a generic interface style
that distracts from the engineering content. Prefer simple rectangular nodes
with straight corners for report figures. A small radius is acceptable when it
has a consistent purpose, but it should not be the default decoration applied
to every shape.

Do not enclose every stage in a large panel. Separate stages with whitespace,
short headings or restrained rules. Remove decorative vertical dividers,
full-width footer lines and any line that could be mistaken for a connector or
rendering artifact. Do not place a title, subtitle or footer inside the image
when the report already provides that context through its heading and caption.

Align nodes to a consistent grid. Use equal internal padding and deliberate
spacing between related steps. Keep node outlines and connectors thin, normally
around 1 to 1.5 pixels at export scale. Use one arrowhead style. Prefer straight
or orthogonal connectors with a small number of bends. Use curves only when an
orthogonal route would cross content or make the direction ambiguous.

Place connector labels close to their line without placing text on top of it.
Keep arrow direction obvious and avoid unexplained lines that enter a node from
an unexpected side. A loop must visibly return to the repeated operation and
should carry a short causal label such as "No forward progress".

Use left-aligned text inside ordinary technical nodes. Reserve centered text for
very short labels or compact symbols. Write headings in sentence case and use
capital letters only for acronyms. Use a conventional sans-serif typeface and a
consistent hierarchy. Primary node labels may be semibold. Secondary details
should be smaller and quieter. Do not vary font size, weight or alignment merely
for decoration.

Use color only to encode meaning. Keep ordinary nodes neutral. Reserve a small
palette for the trigger, defective operation and demonstrated impact. Reinforce
every color with a label, border or line style so the diagram remains readable
for people with color-vision deficiencies and when printed in grayscale. Avoid
mixing unrelated colors inside one node.

The final figure should look like an engineering diagram, not a dashboard,
marketing infographic or slide template. Avoid generic icon sets, ornamental
callouts, repeated feature-card layouts and decorative polish that is unrelated
to the vulnerability. Precision, information density and clear relationships
should define the visual identity.

Review the image at full size and in the actual Markdown preview. Check that all
text remains readable after scaling, no connector crosses a label, arrows reach
the intended nodes and semantic colors retain sufficient contrast. Ask whether
each line, border, fill and note contributes information. Remove it when the
answer is no.

Export a PNG on a white background using a conventional aspect ratio when the
content allows it. Keep the file below 2 MB and use descriptive alternative
text in Markdown. Preserve the editable vector source in the project working
files, but attach only the final render unless the source would help the vendor
verify or modify the figure. Recalculate and update the attachment SHA-256 after
every image revision.

Before submission, upload the PNG through Bugcrowd and replace the local preview
path with the Markdown embed generated by the platform. Verify the hosted image
once more in the final description field.

## Required structure

Use this sequence unless the program form requires a different presentation.
The headings are not mandatory. Combine adjacent sections when this improves
the flow and avoids repeating the same evidence.

1. **Title**
   Name the attack surface, affected component and demonstrated impact. A good
   title is specific, such as "Cyclic TLS 1.3 certificate parsing exhausts the
   DPI worker pool and blocks new inspected connections".
2. **Overview**
   Explain the defect, the attacker position, the required configuration and
   the observed result in one or two short paragraphs.
3. **Tested environment**
   Record the exact product, firmware version, build, model, architecture,
   license state and relevant security mode. Identify any rule or feature that
   must be enabled. State whether the runtime build differs from the build
   used for static analysis.
4. **Attack scenario and prerequisites**
   Describe who controls each endpoint, how traffic reaches the vulnerable
   parser and what action a protected user must take. Make network reachability
   and authentication requirements explicit.
5. **Reproduction**
   Provide a clean baseline followed by numbered steps. Include exact commands,
   protocol fields, input lengths, timing and stop conditions. The procedure
   must work without access to this workspace or to local file paths.
6. **Evidence**
   Present the smallest set of logs, traces, screenshots and tables that proves
   the path and the impact. Give UTC timestamps so evidence from different
   machines can be correlated.
7. **Demonstrated impact**
   Compare baseline and triggered behavior. State which service, users and
   traffic class are affected. Record duration, recovery and whether retries
   can maintain the condition. Define the exact scope covered by the evidence.
   Explain the visible result in ordinary operational terms. This material may
   be integrated into the evidence section when a separate heading adds no
   clarity.
8. **Root cause**
   Explain the parser or state error in plain language. Add the binary path,
   binary hash, module offsets, relevant call chain, integer conversions and
   missing validation when available. Keep decompiler output short and connect
   every code detail to a runtime observation.
9. **Test boundaries and cleanup**
   Record the bounds used during testing and the restoration result. Include
   only unresolved questions that change severity, reachability or version
   attribution.

## Data the vendor needs

Before submission, confirm that the report contains these facts when they are
relevant:

- Exact product version, build, platform and deployment model
- Affected feature and the configuration needed to reach it
- Affected binary and library paths with SHA-256 hashes
- Network direction, source role, destination role, protocol and port
- Authentication and user interaction requirements
- Exact trigger input or a deterministic generator for it
- Baseline behavior using the same route and configuration
- Process identifiers, worker count and instrumentation points
- Return values, errors, signals, CPU, memory and listener observations
- Logs, crash files, cores, supervisor activity and recovery time
- Number of attempts and whether the result was deterministic
- Difference between observed impact and possible wider impact
- Confirmation that secrets and unrelated customer data are absent

For a denial of service, a stopped test is not enough by itself. Show that an
unrelated control flow failed or became materially slower while the vulnerable
condition was active. Distinguish a single rejected request from worker
exhaustion, service restart and appliance-wide loss of availability.

## Evidence and attachments

Attach a minimal proof of concept, a short representative trace and screenshots
or a video when they make reproduction easier. Give every attachment a clear
name and explain what it proves. Scripts should use documented arguments and
bounded defaults. They must not contain credentials, private keys, local absolute
paths or infrastructure that the vendor cannot reproduce.

Prefer small evidence blocks placed next to the claim they support. For
example, show the malformed field as annotated bytes, the vulnerable operation
as a short pseudocode fragment, worker behavior as a before and after table,
and the end-to-end route as a simple diagram. Do not make the reviewer search
through an attachment to find the primary proof.

Do not paste entire debug logs into the report. Preserve full logs as
attachments and quote only the lines that establish the claim. Include hashes
for generated payloads and important artifacts. Check that screenshots do not
reveal passwords, tokens, email addresses or unrelated identifiers.

The Bugcrowd description is limited to 25,000 characters. Keep the main report
self-contained and reserve bulky raw evidence for attachments. Complete the
initial submission before sending it. A vague placeholder can be rejected, and
Bugcrowd states that a submitted report cannot be edited through the original
form.

## Final acceptance check

Before submission:

1. Read the current program brief and confirm the exact target is in
   scope. The live brief takes precedence over this file.
2. Select the closest VRT category without using the category as proof of
   severity.
3. Confirm that a fresh engineer can reproduce the issue from the report and
   attachments alone.
4. Verify that every security claim points to an observation.
5. Remove speculative escalation paths from the title and demonstrated impact.
6. Check version attribution carefully. Do not present one build as runtime
   proof for another build.
7. Check the report and every attachment for secrets and local links.
8. Keep the finding confidential and respond quickly if triage requests more
   information.

## Official references

- [Bugcrowd, Reporting a Bug](https://docs.bugcrowd.com/researchers/reporting-managing-submissions/reporting-a-bug/)
- [Bugcrowd, Embedded Images for Submissions and Comments](https://docs.bugcrowd.com/researchers/reporting-managing-submissions/reporting-a-bug/embedded-images-for-submissions-and-comments/)
- [Bugcrowd, Viewing the Engagement Brief](https://docs.bugcrowd.com/researchers/engagement-brief/viewing-engagement-brief/)
- [Bugcrowd, Standard Disclosure Terms](https://www.bugcrowd.com/resources/hacker-resources/standard-disclosure-terms/)
- [Bugcrowd, Code of Conduct](https://www.bugcrowd.com/resources/hacker-resources/code-of-conduct/)
- [Bugcrowd, Vulnerability Rating Taxonomy](https://bugcrowd.com/vulnerability-rating-taxonomy)
