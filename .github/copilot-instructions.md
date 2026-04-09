## Design Context

### Users
Medicare beneficiaries (65+), primarily on fixed incomes, visiting year-round after receiving a touchpoint (SMS, email, mail, phone call). They browse on tablets and larger phones during daytime hours. Emotionally, they arrive cautiously optimistic but skeptical — "is this really free? what's the catch?" Many are confused by healthcare complexity and grateful for someone who simplifies it. They want to save money without compromising care quality.

### Brand Personality
**Reassuring, straightforward, neighborly.**

The tone is a trusted friend explaining how something works over coffee — not a corporation selling a product. Warm but not cutesy, clear but not dumbed-down. We're talking to people's parents and grandparents. The takeaway emotion: "This is simple, it's free, and I have nothing to lose — I'd be leaving money on the table if I didn't use this."

### Aesthetic Direction
- **Theme**: Light mode only. High readability in well-lit environments is the priority.
- **Warmth over clinical**: The site should feel like a healthcare program that genuinely cares, not a fintech dashboard or hospital system. Slightly softer edges, friendly illustrations/icons rather than purely clinical ones.
- **Color**: Current teal/wine palette is not locked in. Open to evolving toward softer, warmer tones — possibly pastels or lighter tints. The palette should feel approachable and calming, not corporate or sterile.
- **References**: Oscar Health (clean, friendly, makes insurance less intimidating), GoodRx (approachable, savings-forward), One Medical (modern but warm).
- **Anti-references**: Traditional Medicare supplement sites (Humana, Aetna Medicare pages — corporate, cluttered, overwhelming fine print). Nothing that looks like a Silicon Valley startup targeting 25-year-olds.

### Accessibility Requirements
- **WCAG AA minimum**, AAA for text contrast where feasible — non-negotiable given 65+ audience.
- Base font size 16px minimum, preferably 18px for body text.
- Generous line height.
- Large tap targets: minimum 44x44px.
- Reduced motion by default (respect `prefers-reduced-motion`).
- Clear form labels, visible focus states.
- Screen-reader friendly provider search results.

### Design Principles

1. **Defuse skepticism immediately.** Every design choice should build trust. No flashy gimmicks, no visual complexity that feels like it's hiding something. Clarity is the strongest trust signal.

2. **Warmth without patronizing.** The audience is older, not less capable. Design should be welcoming and easy to navigate without feeling dumbed-down or overly large. Respect their intelligence while respecting their needs.

3. **Savings made tangible.** The core value prop — "you save money by using quality doctors" — should feel concrete and real, not abstract. Design should make the benefit feel immediate and certain.

4. **Simplicity as a feature.** The program is genuinely simple. The design should reflect that simplicity rather than adding visual complexity that contradicts the message. Every element earns its place.

5. **Neighborly, not corporate.** This should feel like a local service that knows your name, not a national insurance company. Human scale, warm tone, approachable in every detail.
