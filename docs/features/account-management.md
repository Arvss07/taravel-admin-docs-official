# Account Management

The Account Management section handles both organization accounts and individual accounts, including sub-accounts. It includes credential generation, status control (active/blocked), organization details, and pagination with filtering.

## Overview

- **Account Types**: Organization and Individual
- **Service Types**: Bus or Van
- **Sub-Accounts**: Create accounts under an organization
- **Credentials**: Securely generate credentials and view them in a modal
- **Status Control**: Active / Blocked with audit fields
- **Filtering & Search**: By status, account type, service type, plus search in table
- **Pagination**: Client-side paging per current dataset

## CRUD Operations

### Create
- Add Organization or Individual
- For Organization: sub-accounts can be added after creation
- Credentials: generate and show via Credential Modal (copy-once UX)

### Read
- List view with pagination and filter panel
- Table supports in-row actions: view, edit, add sub-account, delete
- Detail modals for Organization and Individual accounts

### Update
- Edit account status (active/blocked)
- Edit account details (contact info, display name, service type)
- Edit organization details and manage sub-accounts

### Delete
- Delete account (with confirmation modal)
- Cascade considerations: sub-accounts visibility and organization relations

## Search & Filtering

### Search (table-level)
- Search across `displayName`, `username`

### Filters (slice-level)
- **Status**: all, active, blocked
- **Account Type**: organization, individual
- **Service Type**: all, bus, van

### Pagination
- Page, pageSize with hasNextPage/hasPrevPage indicators

## Data Flow

### Account Management Architecture

```mermaid
graph TB
    subgraph Page[Account List Page]
        ALP[AccountListPage]
        Table[AccountTable]
    end

    subgraph Modals[Modals]
        AddAcc[Add Account]
        AddSub[Add Sub-Accounts]
        Cred[Credential Modal]
        EditStatus[Edit Status]
        OrgView[Organization Details]
        IndView[Individual Details]
    end

    subgraph State[State Management]
        Redux[Redux Store - UI State]
        TQ[TanStack Query - Server State]
    end

    subgraph Data[Data Sources]
        FS[Firestore Accounts]
        VT[Vehicle Types]
        Cache[Query Cache]
    end

    ALP --> Table
    ALP --> AddAcc
    ALP --> AddSub
    ALP --> Cred
    ALP --> EditStatus
    ALP --> OrgView
    ALP --> IndView

    ALP --> Redux
    ALP --> TQ
    TQ --> FS
    TQ --> VT
    TQ --> Cache
```

## Usage Guide

### Managing Accounts
1. Open Accounts in the sidebar
2. Adjust filters (status, account type, service type)
3. Use table search to find specific accounts
4. Use actions to View / Edit / Add Sub-Account / Delete

### Credential Handling
- Use the Credential Modal to view generated credentials
- Copy credentials securely; they may not be shown again

## Troubleshooting

- **Accounts not updating?** 
  - Check TanStack Query cache - data may be cached
  - Use browser DevTools to inspect query cache
  - Try manual refresh or clear query cache
- **Search not finding expected results?** 
  - Check filters and search field
  - Verify query parameters are correct
- **Permission errors?** 
  - Ensure admin authentication and role
  - Check Firebase security rules
- **Slow loading?**
  - Check network tab for failed requests
  - Verify query keys are properly configured
  - Consider adjusting stale time settings

---

*Next: Learn about [User Management](user-management.md).*
