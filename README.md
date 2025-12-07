# Analysis Neptune.ai

## Core

A product for analyzing the training stage of LLM models. Features fast ingestion of metrics, their storage, and BI-style dashboards.

Currently was scheduled to be discontinued on March 5, 2026 (https://docs.neptune.ai/transition_hub/). The inial analysis was conducted before the discontinuation plans were known.

## Key Components

* Ingestion through Kafka
* Metrics storage in ClickHouse
* General database - MySQL (we would use PostgreSQL instead)
* Application to query and build dashboards
* Kubernetes for deployment

All stack components are valid except for MySQL. There's no compelling reason to choose it over PostgreSQL.

## References I Would Do Before Developing Such a System

### UI

* Block-based dashboard builder
* Formula builder
* Chart builder

### Backend

* Prototype of ingestion to ClickHouse through Kafka
* Formula expressions to ClickHouse queries
* Load testing on ingestion and querying

## Documentation We Would Like to Have

* Chart types
* How formula expressions work
* How dashboards/reports work

## Features to Defer for the First Version

* Deployment guides
* Multi-tenancy
* Authentication/roles
* Drill-down functionality
* Fullscreen expansion
* Keyboard shortcuts

## Recommendations

I would recommend making the new product compatible with Neptune so its open-source components could be reused (neptune-query, neptune-exporter, neptune-client-scale, neptune-api, neptune-examples). This will reduce the development effort and allow us to inherit the expertise backed by Neptune's team in these libraries. Additionally, it would be great to make our app Neptune-compatible, so Neptune's app could work with our backend and vice versa. Neptune doesn't have a free tier but has a publicly available demo app (https://scale.neptune.ai/o/examples/org/LLM-Pretraining). I would recommend starting with a fully compatible system and diverging only when ready for a heavy investment in product development. Simply maintaining compatibility is much easier and still provides value. Divergence could be considered once there's investment, a strong vision, or specific customer requirements.

## Possible Approaches

I assess that our expertise in backend development is stronger than in UI, so one possible approach is to create a simple mock that mimics Neptune's backend API and start developing the UI first. Different features can then be disabled via feature flags during real backend development. This way, we start with the riskiest part for us — the UI — and then gradually develop the backend, enabling feature flags as relevant backend components are completed.

# Positioning

Future development may vary, but I would recommend initial positioning as an open-source alternative to Neptune that is compatible with it.

Update: Neptune was scheduled to be discontinued on March 5, 2026 so it may be positioned as a smooth replaicement.

## Links

* https://scale.neptune.ai/o/examples/org/LLM-Pretraining
* https://docs.neptune.ai/

