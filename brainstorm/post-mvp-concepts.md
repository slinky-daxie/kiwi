# Post-MVP Concepts

*Ideas for evolution beyond the human-in-the-loop MVP*

---

## Context

The MVP focuses on **agent assistance** with 100% human-in-the-loop. These are concepts for what could come next, based on:
- Learning from MVP data
- Building on proven value
- Expanding use cases for the same core technology

**Note**: These are exploratory ideas, not commitments. Real decisions would be based on MVP results and business priorities.

---

## 1. Selective Automation

**Concept**: Let high-confidence cases auto-execute after customer approval

**How it works:**
- System generates resolution with >95% confidence
- Customer receives SMS/email: "Your flight is delayed. We can rebook you on BA789. Tap to approve."
- Customer approves → automatic execution
- Low-confidence cases still go to human agents

**Why interesting:**
- Leverages confidence scores from MVP learning
- Customer stays in control (they approve)
- Reduces agent workload for straightforward cases
- Scales support without scaling headcount proportionally

**Open questions:**
- What confidence threshold is safe enough?
- Which case types are suitable? (Simple rebookings? Refunds? Complex multi-leg?)
- How do customers feel about automation vs human touch?

---

## 2. Customer-Facing Applications (Transparency)

**Concept**: Reuse the same RAG stack for customer self-service

**Why this matters:**
Research finding: *"Customers say the guarantee covers nothing"* → transparency gap

**Potential applications:**

### Guarantee Explainer
- **Pre-purchase**: "Does my itinerary qualify? What does it cover?"
- **During trip**: "Does my guarantee cover this delay?"
- **Post-issue**: "Why was my claim handled this way?"

Uses same RAG infrastructure (policies, rules, historical cases) but surfaces it to customers directly.

### Risk Dashboard
- Show customers: "This connection is medium risk (1h buffer at busy airport)"
- Provide transparency about booking choices
- Help customers make informed decisions about guarantee purchase

### "What If?" Tool
- "What if I miss my connection?" → Shows coverage, typical resolution, customer cost
- Educates customers before they book
- Reduces support volume for simple questions

**Why interesting:**
- Same technology serves both agents AND customers
- Addresses research finding about trust/transparency
- Could increase guarantee attachment through education (not manipulation)
- Reduces "what does my guarantee cover?" support tickets

**Open questions:**
- Does transparency increase or decrease guarantee sales?
- Where to surface this? (In-app? Web? Email?)
- Risk of overwhelming customers with too much information?

---

## 3. Proactive Resolution

**Concept**: Contact customers BEFORE they contact us

**How it works:**
- System detects flight delay/cancellation via monitoring
- Cross-references with booking database → identifies affected customers
- Generates resolution options automatically
- Proactively sends: "We've detected your flight is delayed. Here are your options..."

**Why interesting:**
- Transforms customer experience from reactive to proactive
- Reduces support volume (customer doesn't need to contact us)
- Customers impressed when we solve problems before they notice them
- Reduces "in-airport emergency" cases (most stressful scenario)

**Open questions:**
- How much proactive communication is helpful vs annoying?
- Customer communication preferences (SMS? Email? Push notification?)
- What if prediction is wrong? (False alarms damage trust)

---

## 4. Predictive Features

**Concept**: Predict issues before they happen and prevent them

### Risk Scoring at Booking
- Show customers upfront: "This itinerary has medium connection risk"
- Suggest: Add guarantee, or see safer alternatives
- Helps customers make informed choices

### Pre-emptive Rebooking
- Detect: First flight likely to delay → customer will miss connection
- Proactively hold alternative flight
- Notify customer with pre-booked option
- Customer approves → seamless switch, no disruption

### Smart Routing Recommendations
- Score itineraries by: price + convenience + risk
- Recommend optimal balance
- Example: "€30 more expensive, but 40% lower risk and 2h faster"

**Why interesting:**
- Shifts from "fixing problems" to "preventing problems"
- Uses data we're already collecting (flight performance, connection success rates)
- Better customer experience (less stress)
- Could reduce overall disruption volume

**Open questions:**
- Do customers trust AI predictions about risk?
- How accurate do predictions need to be to be useful?
- Does showing risk scare customers away from bookings?

---

## 5. Multi-Agent Systems

**Concept**: Specialised AI agents working together, not just one LLM

### Potential Agent Roles:

**Negotiation Agent:**
- Talks to airline APIs on behalf of customer
- Requests compensation, upgrades, lounge access
- Knows airline-specific policies

**Personalization Agent:**
- Learns customer preferences over time
- "This customer always picks window seats, prefers morning flights"
- Tailors resolution options to individual preferences

**Sentiment Analysis Agent:**
- Detects frustration in customer messages
- Escalates emotionally charged cases to senior agents
- Adjusts communication tone based on sentiment

**Context Enrichment Agent:**
- Continuously gathers external data (weather, airport congestion, strikes)
- Enriches LLM reasoning with real-time intelligence
- Predicts cascading failures

**Why interesting:**
- More sophisticated than single-LLM approach
- Each agent specialises in one task (vs general-purpose)
- Demonstrates advanced AI architecture understanding
- Could handle more complex scenarios

**Open questions:**
- Is this over-engineering? Could simpler approaches work?
- How do agents coordinate? (Orchestration complexity)
- What's the incremental value vs single LLM?

---

## 6. B2B Platform / Ecosystem

**Concept**: Transform internal tool into external product

### Potential approaches:

**White-Label for OTAs:**
- Package the CS automation system
- Sell to other travel agencies
- Customise for their policies/branding

**API for Insurance Companies:**
- Real-time risk scoring
- Claim validation automation
- Dynamic pricing based on itinerary risk

**Airline Partnerships:**
- Share disruption data (anonymised)
- Airlines get early warning of cascading delays
- Pineapple Travel gets priority rebooking access

**Industry Knowledge Sharing:**
- Anonymised resolution patterns shared across industry
- Position Pineapple Travel as thought leader
- "What works" best practices database

**Why interesting:**
- Creates new revenue stream from existing technology
- Positions company as industry leader
- Network effects: More data = better models
- Platform thinking: Build once, leverage everywhere

**Open questions:**
- Is this too early? (Need to prove internal value first?)
- What's the right business model? (SaaS? Per-transaction? Enterprise?)
- Security concerns with multi-tenancy?
- Does this distract from core business?

---

## Common Themes Across Concepts

1. **Progressive autonomy**: Start human-in-the-loop, gradually increase automation based on trust
2. **Reusable infrastructure**: Same RAG/LLM stack serves multiple use cases
3. **Transparency as feature**: Use AI to educate customers, not just automate
4. **Proactive not reactive**: Shift from "fixing problems" to "preventing problems"
5. **Platform thinking**: Build once, leverage everywhere (agents, customers, partners)

---

## What to Emphasise at Interview

**Good to mention:**
- Customer-facing applications (addresses research finding about transparency)
- Selective automation (shows understanding of gradual autonomy)
- Proactive features (innovative, customer-focused)

**Mention with caution:**
- Multi-agent systems (could sound like over-engineering if not framed carefully)
- B2B platform (could seem like distraction from core business)

**How to frame:**
"These are ideas we could explore AFTER the MVP proves value. Real decisions would depend on:
- What we learn from agent and customer feedback
- Which problems are most impactful to solve
- Business priorities and resources
I'm not attached to any specific path - I'd let the data guide us."

---

## Questions for Exploration

1. Which concept would deliver most customer value for least complexity?
2. Are we trying to do too much? Should we focus on mastering one area first?
3. What assumptions need to be validated before pursuing each concept?
4. What could we learn from MVP that would inform which direction to go?
5. Which concepts are "nice to have" vs "game changing"?

---

*These are exploratory concepts for discussion, not detailed plans or commitments.*

