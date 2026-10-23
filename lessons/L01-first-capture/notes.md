
# L01 — First Capture Evidence Notes

**Status:** In progress  
**Evidence source:** My own Wireshark capture  
**Purpose:** Record observed DNS and TCP activity without assuming unverified results.

## 1. DNS Investigation

### A Record

- Domain queried: `facebook.com`
- Query frame: 34
- Response frame: 35
- Transaction ID: `0x0002`
- Query-response transaction ID match: Confirmed
- Response code: No error
- Answers section: Records present
- TTL observed: 20 seconds

### AAAA Record

- Domain queried: `facebook.com`
- Query frame: 36
- Response frame: 37
- Transaction ID reported: `0x0003`
- TTL observed: 25 seconds
- Query-response transaction ID match: Needs explicit reconfirmation

### DNS Response Timing

Two response-time values were observed:

- `0.071615000` seconds
- `0.040356500` seconds

The mapping of these values to the A and AAAA responses must be verified against the corresponding packets before finalizing the timing comparison.

### DNS Findings

The capture contains A and AAAA queries and their corresponding response packets. The original A query received a response reporting no error, with answer records present.

These observations describe this capture only. They do not establish persistent DNS behavior.

## 2. TCP Investigation

### Initial SYN Observation

- Filter used: `tcp.flags.syn == 1 && tcp.flags.ack == 0`
- Initial SYN frame: 82
- Source IP: Redacted in this public report
- Destination IP: Redacted in this public report
- Destination port: 80
- Info-column text: Not recorded

### Pending Investigation

- Identify the SYN-ACK response, if present in the capture.
- Check for the subsequent ACK.
- Record verified frame numbers and TCP flags.
- Determine whether the available packets support concluding that the handshake completed.

## 3. Limitations

This investigation is still in progress. No conclusion about TCP handshake completion has been made.

Only observations verified in the capture will be added to the final report.

## 4. GitHub Deliverable

This file records the preliminary evidence for Lesson 1. It will be updated as additional observations are verified.
