
A PROJECT COMPILING ALL MY SKILL SET.

..named after the person I love the most.

**System Design: MOTHER INFRASTRUCTURE**

---

### Core Technologies

- **Frontend:** React / NextJS
- **Backend:** GraphQL / RESTful API
- **Database:** Prisma + PostgreSQL + MongoDB
- **Containerization & Orchestration:** Docker + Kubernetes

---

### Architecture Overview

#### Frontend

**Container Structure:**
- `[gateway]`: Main container hosting the frontend
- `[render1]` to `[render5]`: On-demand React runtimes that load individual large-scale pages. These are:
  - Not hosted online independently
  - Not connected to the server directly
  - Used for dynamic runtime rendering only when users navigate to certain frontend pages

**Advantages:**
- Scalable
- Lightweight main container
- Reduced load by only invoking render containers as needed

---

#### Backend

**Container Structure:**
- `[gateway]`: Entry point container that handles all incoming server requests
- `[ss1]` to `[ss5]`: Separated API containers
  - These run specific parts of the backend logic
  - Kubernetes handles auto-scaling
  - Only *overloaded containers* are replicated, not the entire server system

**Design Pattern:**
- Follows the *separated API* methodology
- Efficient resource allocation
- Better performance & cost optimization

---

#### Database

**Structure:**
- `[gateway]`: Database gateway with **manual load balancer**
- `[shard1]`, `[shard2]`, `[shard3]`: Individual DB shards
  - Within each shard:
    - `[partitioned data 1]`
    - `[partitioned data 2]`
    - `[partitioned data 3]`

**Routing Logic:**
- Gateway manually redirects requests to the **least loaded DB server**
- Uses sharding + partitioning based on request type and origin
- Prioritizes fast lookups and high availability

**Advantages:**
- Reduces DB bottlenecks
- Optimized for large-scale traffic
- Full control over load distribution

---

#### Admin Panel

- Built with **vanilla NextJS**
- Runs in its own isolated container
- Purpose:
  - Modify original database entries
  - Perform admin-level tasks only
- Lightweight, secured, and not part of user-serving infra

---

### Summary

This infrastructure was designed for:
- Maximum scalability
- Cost-efficient operation
- Resilient performance
- Fine-grained load control

**Unique Highlights:**
- Manually controlled database load balancer
- Sharded & partitioned DB for micro-second reads
- Frontend render separation for optimized runtime delivery
- Dynamic backend container scaling

> "A custom, senior-level architecture built with intention, in just one week."

---

Ready for diagram & PDF packaging.

