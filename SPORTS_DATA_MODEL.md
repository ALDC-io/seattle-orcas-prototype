# World-Class Sports Franchise Data Architecture

## Industry Benchmarks

### NFL (90B+ daily fan attributes)
- **Platform**: AWS-based cloud ecosystem
- **Scale**: Petabytes annually, billions of data points per game
- **Key Partners**: AWS, NetApp (data infrastructure)
- **Focus**: Unified first-party fan profiles, marketing triggers

### NBA
- **Platform**: Microsoft Azure cloud + data lake
- **Features**: AI-based personalization, churn prediction, game recommendations
- **Key Partners**: Microsoft
- **Focus**: Streaming platform, fan personalization

### Manchester City / City Football Group
- **Platform**: SAP (HANA, Analytics Cloud, Sports One)
- **Scale**: 10+ years of detailed game data
- **Features**: SAP Challenger Insights (opponent analysis), real-time coaching tools
- **Key Partners**: SAP, Opta (sports data)
- **Focus**: On-field performance + fan engagement

---

## Sports Franchise Data Categories

### 1. Player Performance Data
| Data Point | Source | Update Frequency |
|------------|--------|------------------|
| Match statistics | League/CricViz | Real-time |
| Training metrics | Wearables | Daily |
| Fitness/injury | Medical staff | As needed |
| Historical performance | Database | Ongoing |
| Opposition analysis | Scouting | Pre-match |

### 2. Fan Engagement Data
| Data Point | Source | Update Frequency |
|------------|--------|------------------|
| Social media metrics | Platform APIs | Hourly |
| Ticket purchases | Ticketing system | Real-time |
| Merch sales | POS/E-commerce | Real-time |
| App engagement | Mobile analytics | Daily |
| Email/SMS response | Marketing platform | Per campaign |
| In-stadium behavior | WiFi/beacons | During events |

### 3. Operations Data
| Data Point | Source | Update Frequency |
|------------|--------|------------------|
| Event logistics | Event management | Per event |
| Staffing | HR/scheduling | Weekly |
| Vendor performance | Contracts/invoices | Monthly |
| Facility maintenance | Work orders | As needed |
| Community programs | Program tracking | Weekly |

### 4. Commercial/Sponsorship Data
| Data Point | Source | Update Frequency |
|------------|--------|------------------|
| Sponsor impressions | Media tracking | Per campaign |
| Brand visibility | Social listening | Daily |
| Activation performance | Event tracking | Per activation |
| Contract deliverables | CRM | Ongoing |
| Revenue attribution | Finance | Monthly |

---

## Key Platform Providers

### KORE Software (Two Circles)
- **Specialty**: Sponsorship management + fan engagement
- **Features**: 360° fan view, ticketing analytics, sponsorship ROI
- **Clients**: NFL, MLB, NBA teams

### EngageRM (Microsoft Dynamics)
- **Specialty**: CRM for sports/entertainment
- **Features**: 50+ integrations, AI/ML, centralized ops
- **Clients**: Various sports organizations

### Salesforce Sports Cloud
- **Specialty**: B2B2C data model for franchises
- **Features**: Season ticket management, sponsorship sales, incident tracking

### Databricks
- **Specialty**: Data lake + ML platform
- **Scale**: 50M+ data points daily processing
- **Features**: AutoLoader, Delta Lake, predictive analytics

---

## Seattle Orcas Data Landscape (Current State)

### What They Likely Have
| System | Purpose | Data Quality |
|--------|---------|--------------|
| MLC league stats | Player performance | Good (provided) |
| Social media | Fan engagement | Fragmented |
| Ticketing platform | Sales data | Basic |
| Spreadsheets | Operations | Manual |
| Partner reports | Sponsorship | Inconsistent |

### What They Need (Enterprise Intelligence)
1. **Unified Data Layer** - Single source of truth
2. **Decision Tracking** - What worked, what didn't
3. **Pattern Recognition** - Identify success drivers
4. **ROI Attribution** - Prove sponsor value
5. **Fan 360° View** - Unified fan profiles

---

## Proposed Data Model for Prototype

### Core Entities

```
PLAYERS
├── player_id (PK)
├── name
├── role (batter/bowler/all-rounder/wicketkeeper)
├── nationality
├── batting_hand (left/right)
├── bowling_style
├── jersey_number
├── headshot_url
└── stats (JSON)
    ├── matches
    ├── runs
    ├── wickets
    ├── average
    ├── strike_rate
    └── economy

MATCHES
├── match_id (PK)
├── opponent
├── date
├── venue
├── result (win/loss)
├── score
└── highlights (JSON)

PLAYER_PERFORMANCE
├── performance_id (PK)
├── player_id (FK)
├── match_id (FK)
├── runs_scored
├── balls_faced
├── wickets_taken
├── overs_bowled
├── catches
└── performance_rating

FAN_ENGAGEMENT
├── engagement_id (PK)
├── date
├── social_mentions
├── social_sentiment
├── ticket_sales
├── merch_revenue
├── app_active_users
└── email_open_rate

DECISIONS
├── decision_id (PK)
├── date
├── category (marketing/operations/player/sponsor)
├── description
├── expected_outcome
├── actual_outcome
├── success (boolean)
└── learnings

SPONSORS
├── sponsor_id (PK)
├── name
├── tier (principal/jersey/partner)
├── contract_value
├── deliverables (JSON)
├── impressions_delivered
└── roi_score
```

---

## Visualization Tiers for Athena

### Cricket Team Structure

**Tier 1: Leadership**
- Captain (Heinrich Klaasen)
- Vice-Captain (Harmeet Singh)

**Tier 2: Star Players (International)**
- David Warner (AUS)
- Shimron Hetmyer (WI)
- Fazalhaq Farooqi (AFG)
- Kyle Mayers (WI)
- Sikandar Raza (ZIM)
- Gerald Coetzee (SA)
- Obed McCoy (WI)

**Tier 3: Core Squad**
- Bjorn Fortuin
- Josh Brown
- Aaron Jones
- Steven Taylor
- Gulbadin Naib

**Tier 4: Domestic/Development**
- Harmeet Singh
- Shayan Jahangir
- Sujit Nayak
- Rahul Jariwala
- Cameron Gannon
- Waqar Salamkheil

### Role-Based Groupings

**Batters (Offensive)**
- Warner, Hetmyer, Klaasen, Taylor, Jones, Brown, Nayak

**Bowlers (Defensive)**
- Farooqi, McCoy, Coetzee, Fortuin, Gannon, Salamkheil

**All-Rounders (Hybrid)**
- Raza, Mayers, Naib, Harmeet Singh

**Wicketkeepers (Special)**
- Klaasen, Jahangir, Jariwala

---

## Enterprise Intelligence Features

### Decision Tracking Dashboard
- Log all operational decisions
- Track outcomes vs expectations
- Identify patterns in successes/failures
- Generate recommendations

### Sponsorship ROI Calculator
- Track impressions delivered
- Compare to contract deliverables
- Calculate value generated
- Generate partner reports

### Fan Engagement Optimizer
- Unified fan profile view
- Segment by engagement level
- Personalized campaign recommendations
- Churn prediction

### Player Performance Analyzer
- Individual contribution metrics
- Team impact scoring
- Opponent matchup analysis
- Selection recommendations
