## GitView Api

The GitView Api is exclusive to paying customers for the Git Analytics platform [GitView.com](https://gitview.com/)

- [Retrive Api Key](#retrive-api-key)
- [Get Contributor Parents](#get-contributor-parents)
- [Get Timeline Data](#get-timeline-data)

### Retrive Api Key

Your key can be found in the Billing & Other Settings Section of your GitView Organization

### Get Contributor Parents

Returns Contributor Parents (or for all intents and purposes simply Contributors) which comprising of 1 to many git contributors that have been linked together.

#### Params

- api_key
- organization_id
- contributors
  - all: returns all contributor parents no matter if they have been active or not
  - recent (default): returns contributor parents that have a contributor that was active in last month 

#### Example Request

```bash
curl "https://app.gitview.com/organizations/<organization_id>/contributor_parents?api_key=<key>"
```

#### Example Response

```json
[
  {
    "id": "9219bb45-5a59-4cf9-9fd9-54fcd1c79950",
    "name": "coolbot",
    "username": 'coolbot'
  },
  {
    "id": "a023be6a-947e-427d-92cd-d075e5e6ceab",
    "name": "James Ro",
    "username": "jamesro"
  },
  {
    "id": "14592dba-bd1e-4365-bfa3-d1974af21064",
    "name": "Sara Tu",
    "username": "saratu839"
  },
  {
    "id": "a4f21427-e48d-4d98-9627-ddb48c682282",
    "name": "Mike Watkowski",
    "username": "mwat393"
  }
]
```

### Get Timeline Data

Return various data in a timeline fashion

#### Params

- api_key
- organization_id
- begin: begin date to filter on (i.e. 2021-07-20)
- end: end date to filter on (i.e. 2021-09-20)
- period: period to group by
  - week
  - month
  - year
- unit: unit to look up
  - commit
  - impact_no_outliers
  - impact
  - pull_request_merged
  - pull_request_created
  - contributor
  - reviews
  - developer_days
  - prs_created_over_developer_days
- contributor_parent_id: group by specific contributor parent
- repository_id: group by specific repository_id


#### Example Request

```bash
curl "https://app.gitview.com/organizations/<org_id>/timeline?api_key=<key>&begin=2021-07-25&end=2021-10-23&period=week&unit=impact_no_outliers"
```

#### Response Format

```json
[
  {
    "date": "2021-07-19T00:00:00.000Z",
    "value": 3085
  },
  {
    "date": "2021-07-26T00:00:00.000Z",
    "value": 3014
  },
  {
    "date": "2021-08-02T00:00:00.000Z",
    "value": 4385
  },
  {
    "date": "2021-08-09T00:00:00.000Z",
    "value": 3644
  }
]
```
