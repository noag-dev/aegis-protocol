# Aegis Protocol

**Verifiable execution receipts for AI agents.**

Aegis Protocol is an experimental trust layer for AI agent systems.  
It creates signed, tamper-evident receipts that record what an AI agent attempted, what tools it used, what policy checks happened, and whether the action was allowed, blocked, or required human approval.

## Vision

AI agents are moving from simple chat into real action:

- reading data
- calling tools
- sending messages
- editing files
- using APIs
- triggering workflows
- making decisions across systems

As agents become more powerful, organizations need a way to answer one critical question:

> What exactly did the agent do, and can we prove it?

Aegis Protocol aims to make AI agent actions auditable, verifiable, and policy-aware.

## Core idea

Every important agent action should produce an **Agent Receipt**.

An Agent Receipt records:

- agent identity
- user goal
- requested tools
- executed tools
- required permissions
- policy checks
- policy result
- risk level
- input hash
- output hash
- trace hash
- timestamp
- signature

## Example receipt

```json
{
  "receipt_version": "0.1",
  "receipt_id": "rec_001",
  "agent_id": "email_agent",
  "agent_version": "0.1",
  "session_id": "session_001",
  "user_goal": "Send an email to client@example.com saying the invoice is ready.",
  "action_type": "email.send",
  "tools_requested": ["email.send"],
  "tools_executed": [],
  "permissions_required": ["send_external_email"],
  "policy_checks": [
    {
      "rule": "external_email_requires_approval",
      "result": "requires_human_approval"
    }
  ],
  "policy_result": "requires_human_approval",
  "risk_level": "medium",
  "input_hash": "example_input_hash",
  "output_hash": "example_output_hash",
  "trace_hash": "example_trace_hash",
  "previous_trace_hash": null,
  "timestamp_utc": "2026-05-28T00:00:00Z",
  "runtime": "python",

What Aegis is not

Aegis is not:

a blockchain
a token
a chatbot
a model provider
a replacement for security reviews
a guarantee that an AI system is safe

Aegis is a developer tool for producing verifiable records of agent behavior.

First milestone

The first milestone is a local Python SDK that can:

wrap a simulated agent action
check policy rules
generate an Agent Receipt
hash the input, output, and trace
sign the receipt
verify the receipt
save the receipt as JSON

First demo

The first demo will simulate an email agent.

User goal:

Send an email to client@example.com saying the invoice is ready.

Aegis will check whether the agent is allowed to send external emails.

Possible outcomes:

allowed
blocked
requires_human_approval

Then Aegis will generate a signed receipt.

Project status

Current version: 0.1
Current stage: foundation
Current artifact: protocol spec and repository setup

License

MIT License.


  "signature_algorithm": "ed25519",
  "signature": "example_signature"
}
