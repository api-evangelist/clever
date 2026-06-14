# Clever GraphQL API

## Overview

Clever provides a native GraphQL API endpoint alongside its REST API, offering a flexible query interface for K-12 education roster data. The GraphQL API allows application partners to request precisely the data they need in a single request, reducing over-fetching and under-fetching common with REST endpoints.

## Endpoint

```
https://api.clever.com/v3.0/graphql
```

## Authentication

The Clever GraphQL API uses the same OAuth 2.0 bearer token authentication as the REST API. A district-app token is required for most rostering queries. Include the token in the Authorization header:

```
Authorization: Bearer <district_app_token>
```

For SSO and identity queries, a user-scoped bearer token obtained through the OAuth flow is required.

## Key Features

- Query multiple resource types in a single request (districts, schools, students, teachers, sections, courses)
- Paginated connections using cursor-based pagination with PageInfo
- Delta sync via ChangeEvent types aligned with the Events API
- Rich demographic and contact data on student records
- Section enrollment and teacher role resolution in a single query
- Term and course relationships across sections

## Core Types

### Rostering Types

- **District** — Top-level organizational unit; contains schools and admins
- **School** — Individual school within a district; contains sections and staff
- **Student** — K-12 student with demographics, contacts, and enrollment data
- **Teacher** — Educator with section and role assignments
- **Staff** — Non-teaching district or school staff
- **Section** — Class or course section with enrolled students and teachers
- **Course** — Academic course definition linked to sections
- **Term** — Academic term (semester, quarter, year) scoping sections

### Identity and SSO Types

- **Identity** — Unified identity record linking a user across Clever applications
- **SSO** — Single sign-on configuration and state for an application-district pair
- **SSOToken** — OAuth token bundle issued after SSO flow completion
- **Application** — Clever application (partner app) descriptor
- **OAuth** — OAuth 2.0 authorization metadata

### Event and Sync Types

- **Event** — A roster change event (created, updated, deleted)
- **ChangeEvent** — Delta representing a field-level change on a resource
- **DataSync** — Rostering synchronization job and status
- **SyncStatus** — Current state of a district data sync

### Pagination Types

- **PageInfo** — Cursor-based pagination metadata (hasNextPage, endCursor)
- **Connection** — Generic connection wrapper for paginated lists
- **Edge** — Single edge in a connection containing a node and cursor

## Example Query — Students in a School

```graphql
query StudentsInSchool($schoolId: ID!, $first: Int, $after: String) {
  school(id: $schoolId) {
    id
    name
    details {
      ncessId
      lowGrade
      highGrade
    }
    students(first: $first, after: $after) {
      pageInfo {
        hasNextPage
        endCursor
      }
      edges {
        cursor
        node {
          id
          details {
            name {
              first
              middle
              last
            }
            email
            grade
            graduationYear
          }
          demographics {
            race
            hispanicEthnicity
            gender
            ellStatus
          }
        }
      }
    }
  }
}
```

## Example Query — District with Schools and Sections

```graphql
query DistrictRoster($districtId: ID!) {
  district(id: $districtId) {
    id
    name
    status {
      lastSync
      syncEnabled
    }
    schools {
      edges {
        node {
          id
          name
          sections {
            edges {
              node {
                id
                details {
                  name
                  subject
                  period
                }
                course {
                  id
                  details {
                    name
                    number
                  }
                }
                term {
                  id
                  details {
                    name
                    startDate
                    endDate
                  }
                }
                teachers {
                  edges {
                    node {
                      id
                      details {
                        name {
                          first
                          last
                        }
                        email
                      }
                    }
                  }
                }
              }
            }
          }
        }
      }
    }
  }
}
```

## Example Query — Recent Events

```graphql
query RecentEvents($districtId: ID!, $since: String) {
  districtEvents(districtId: $districtId, since: $since) {
    edges {
      node {
        id
        type
        data {
          object
          objectId
          delta {
            key
            previousValue
            currentValue
          }
        }
        createdAt
      }
    }
    pageInfo {
      hasNextPage
      endCursor
    }
  }
}
```

## Rate Limits

The GraphQL endpoint shares the same rate limit pool as the REST API. Clever enforces per-district-app rate limits. Complex queries with deeply nested selections count toward the same limits. Consult the Clever developer documentation for current rate limit values.

## Schema Reference

See `clever-schema.graphql` in this directory for the full GraphQL schema definition including all types, queries, mutations, enums, and input types.

## Resources

- Developer Portal: https://dev.clever.com
- API Reference: https://dev.clever.com/reference
- GraphQL Endpoint: https://api.clever.com/v3.0/graphql
- OAuth Documentation: https://dev.clever.com/docs/integration-types
- Events API: https://dev.clever.com/docs/api-overview
