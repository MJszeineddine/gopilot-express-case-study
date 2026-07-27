# Architecture

> Source code is private/client-confidential. Architecture and implementation details are shared at a safe case-study level.

## System Boundary

GoPilot Express is a delivery operations platform for owners, dispatchers, merchants, and independent couriers. The documented product boundary explicitly excludes GPS, live courier maps, geofencing, background location tracking, company fleet management, fuel modules, and fleet maintenance.

## Main Components

| Surface | Responsibility |
|---|---|
| Web application | Public tracking, role portals, dashboards, reports, bilingual UI |
| API backend | Authentication, authorization, business rules, validation, operational workflows |
| Relational database | Authoritative operational, identity, order, finance, and audit state |
| Worker/process layer | Background cleanup and provider delivery responsibilities |
| Object storage | Private proof/media handling through restricted access patterns |
| Edge/static hosting | Frontend delivery, routing fallback, headers, and domain handling |

## Data And Trust Model

The API is treated as the authority for sensitive operational decisions. Browser input is validated as identifiers and intent; the backend owns quote expiry, order creation, role access, capacity/compliance checks, delivery state changes, COD/reconciliation data, and reporting outputs.

## Operational Lifecycle

1. Merchant profile and pickup data are prepared.
2. A server-authored quote or shipment snapshot is created.
3. Dispatch validates the order and assigns work to an eligible courier.
4. Courier workflow records attempts, delivery outcomes, proof, receiver/signature context, and COD details.
5. Finance/owner views reconcile courier cash, merchant balances, settlements, and operational reports.
6. Public tracking exposes only restricted status data through reference/PIN lookup.

## Public-Safe Stack Summary

- React, TypeScript, Vite, responsive dashboard UI
- FastAPI/Python backend
- Relational database with production-oriented constraints
- Docker/deployment configuration
- CI/release verification and runbook-driven promotion
