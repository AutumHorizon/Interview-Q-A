# System Design Interview Template

## Question
[State the system design question clearly]

## Scale & Requirements
### Functional Requirements
- [ ] Requirement 1
- [ ] Requirement 2
- [ ] Requirement 3

### Non-Functional Requirements
- [ ] Scalability: [specific numbers if given]
- [ ] Availability: [uptime requirements]
- [ ] Consistency: [consistency requirements]
- [ ] Performance: [latency/throughput requirements]

### Scale Estimates
- Users: [number of users]
- Requests per second: [RPS]
- Data size: [storage requirements]
- Bandwidth: [network requirements]

## High-Level Design
[Include a simple diagram or description of the overall architecture]

### Core Components
1. **Component 1**: [Brief description]
2. **Component 2**: [Brief description]
3. **Component 3**: [Brief description]

## Detailed Design

### Database Design
```sql
-- Example schema
CREATE TABLE users (
    id BIGINT PRIMARY KEY,
    username VARCHAR(50),
    created_at TIMESTAMP
);
```

### API Design
```http
GET /api/v1/[resource]
POST /api/v1/[resource]
PUT /api/v1/[resource]/{id}
DELETE /api/v1/[resource]/{id}
```

### Data Flow
1. Step 1: [Describe the flow]
2. Step 2: [Continue the flow]
3. Step 3: [Complete the flow]

## Deep Dive Topics

### Scalability
- How to handle growth
- Horizontal vs vertical scaling
- Load balancing strategies

### Reliability
- Fault tolerance
- Data replication
- Backup strategies

### Performance
- Caching strategies
- Database optimization
- CDN usage

## Follow-up Questions
[Common questions interviewers ask]
1. How would you handle [specific scenario]?
2. What happens if [component] fails?
3. How would you monitor this system?

## Trade-offs Discussed
- Trade-off 1: [Explain the decision]
- Trade-off 2: [Explain the decision]
- Trade-off 3: [Explain the decision]

## Technologies Mentioned
- Database: [chosen database and why]
- Cache: [caching solution and why]
- Queue: [message queue and why]
- Storage: [storage solution and why]

---
*Company: [Where this was asked]*
*Level: [Senior/Staff/etc.]*
*Duration: [Interview length]*
*Video: [Link if available]*
