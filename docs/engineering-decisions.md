# Engineering Decisions

> Source code is private/client-confidential. Architecture and implementation details are shared at a safe case-study level.

## Server-Authoritative Operations

Operational and financial decisions are kept on the backend. The frontend presents workflows and collects user intent; the API validates role access, order transitions, quote validity, COD handling, and report generation.

## Role-Based Product Design

The interface is organized around actual work surfaces: owner oversight, dispatcher coordination, merchant shipment handling, and courier execution. This keeps the product from becoming a generic admin panel and reduces the risk of exposing unrelated data to the wrong role.

## Bilingual And RTL Support

Arabic/English support is treated as a product requirement rather than a late cosmetic change. Layout, navigation, content direction, and responsive behavior need to work across both languages.

## Release Discipline

The documented release approach favors repeatable gates: type checks, linting, frontend and API tests, database checks, browser journeys, deployment verification, archive verification, and production promotion controls.

## Confidential Delivery

The public portfolio shares product architecture and engineering decisions only. Source code, credentials, real customer records, production data, and private deployment details remain unpublished.
