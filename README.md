# Kenya Vaccination Coverage Dashboard

**DTP3 coverage peaked at 91% in 2016. The current figure is 85%. The decline began before COVID and accelerated with it. Eight counties remain below the 70% WHO critical threshold. Mandera sits at 44%.**

---

## What this is

A vaccination coverage analytics project tracking Kenya's immunisation programme across seven antigens from 2000 to 2024. The analysis covers the national trend, county-level coverage gaps for all 46 counties, antigen-by-antigen comparison, East Africa regional benchmarking and the specific question of which antigens have improved, which have declined and how large the current gap to WHO targets is for each.

The headline story — DTP3 at 91% in 2016, now at 85% — is a success narrative with a complication. Kenya built one of the strongest immunisation programmes in East Africa during the MDG period. Then it started declining. Understanding which antigens, which counties and what mechanisms were driving that decline was the analytical question this project set out to answer.

---

## The data

**Primary source: WHO/UNICEF Estimates of National Immunization Coverage (WUENIC)**

The WHO/UNICEF joint reporting process produces annual immunisation coverage estimates for every country, incorporating both administrative data (facility reports) and survey data (DHS, MICS). Published at `who.int/immunization/monitoring_surveillance/data` and accessible through the WHO GHO API.

WHO GHO indicator codes used:

| Antigen | Indicator | WHO GHO Code |
|:---|:---|:---|
| DTP (3rd dose) | DTP3 coverage | `WHS8_110` |
| Measles (1st dose) | MCV1 coverage | `WHS8_117` |
| BCG | BCG coverage | `WHS8_130` |
| Polio (3rd dose) | Pol3 coverage | `WHS8_110` |
| Hepatitis B (3rd dose) | HepB3 coverage | `WHS4_543` |
| Hib (3rd dose) | Hib3 coverage | `WHS8_110` |
| HPV | HPV coverage | `HPV_FVACCINE` |

Kenya WHO GHO API base URL:
```
https://ghoapi.azureedge.net/api/{CODE}?$filter=SpatialDim eq 'KEN'
```

**Secondary sources:**

**Kenya KHIS (Kenya Health Information System)** — facility-level immunisation data by county, available at `hiskenya.org`. Used for county-level disaggregation where WUENIC county estimates were not available.

**GAVI Alliance** — immunisation programme financing data including Kenya's co-financing commitments and new vaccine introductions (HPV 2019, rotavirus 2014, pneumococcal 2011). Published at `gavi.org/programmes-impact/country/kenya`.

**Kenya National Immunisation Policy 2020–2025** — Ministry of Health target framework document. Used as the source for Kenya-specific targets where they differ from WHO global targets.

---

## Five datasets

| Sheet | Rows | What it contains |
|:---|:---|:---|
| `Kenya_National_Trend` | 25 | Annual national coverage 2000–2024 across 7 antigens — DTP1, DTP3, MCV1, MCV2, BCG, Pol3, HepB3 — with WHO 90% target, dropout rate and GAVI milestone markers |
| `Kenya_County_Coverage_2024` | 46 | All 46 counties — DTP3 coverage, MCV1 coverage, BCG coverage, coverage category, region, estimated unvaccinated children, zero-dose children estimate |
| `East_Africa_Regional_2024` | 10 | DTP3 and MCV1 for 10 East African countries — 2024 coverage, % change since 2015, on-track status vs WHO 90% target |
| `Antigen_Gap_Analysis` | 7 | Each antigen — 2016 peak coverage, 2024 current coverage, WHO target, gap to target, % change from peak, trend direction |
| `Zero_Dose_Estimates` | 46 | County-level estimates of zero-dose children (no DTP1) and partially vaccinated children — the equity layer |

---

## What the data showed

**The success story is real — and so is the decline**

Kenya's DTP3 coverage improved from 65% in 2000 to 91% in 2016, a 26 percentage point gain over 16 years. That improvement was real and was driven by cold chain infrastructure investment, community health worker deployment, GAVI new vaccine introductions that brought families into contact with the immunisation system, and the expansion of health facility access under the devolution of health services to county governments in 2013.

The 2016 peak mattered. The programme hit WHO's 90% target that year. Then it fell back.

By 2024, DTP3 sat at 85% — 5 percentage points below the WHO 90% target and 6 below the 2016 peak. The decline started before COVID. The post-2017 trend was downward before 2020 accelerated it. COVID disrupted immunisation services through facility closures, suspension of outreach vaccination campaigns, caregiver reluctance to visit health facilities and supply chain interruptions to cold chain equipment. The 2021 and 2022 recovery was partial, not full.

**The county picture — 73 percentage point gap between best and worst**

Nyeri County: 93% DTP3. Mandera: 44%. That 49 percentage point gap was the defining finding at county level.

Eight counties fell below WHO's 70% critical threshold — the level below which herd immunity for most vaccine-preventable diseases begins to break down: Mandera (44%), Wajir (51%), Garissa (55%), Turkana (58%), Samburu (61%), Tana River (63%), West Pokot (64%) and Marsabit (65%).

These counties were the same cluster that appeared in the maternal health analysis with low ANC4+ coverage. Low immunisation coverage and low maternal health service utilisation were not independent problems in the same counties — they were symptoms of the same underlying barriers: geographic distance, health facility scarcity, pastoralist mobility patterns, low maternal education and health-seeking behaviour shaped by limited prior experience with the formal health system.

**The antigen comparison**

Not all antigens declined equally. BCG — administered at birth in facility — held up well at 88%, because it was tied to facility delivery which was still improving. Vaccines requiring multiple return visits showed more dropout. The DTP1 to DTP3 dropout rate — the proportion of children who received the first dose but not the third — was the most operationally useful indicator, identifying families who had initial contact with the system but did not complete the schedule.

HPV was the newest antigen in the programme (introduced 2019) and the most complex to implement — it required reaching school-age girls through a different contact point than the routine immunisation system. Coverage remained below target in the early years, which was consistent with the pattern for newly introduced vaccines in Kenya.

**Zero-dose children**

The zero-dose estimate — children who received no vaccine whatsoever — was concentrated in the eight critical counties. Kenya had approximately 207,000 zero-dose children in 2023. Reaching them required a different approach than routine immunisation outreach: fixed community vaccination posts were ineffective in pastoral settings where families moved with livestock. What worked in Turkana and Mandera was vaccination linked to other services — nutrition programmes, antenatal care visits and mobile health units — rather than standalone campaigns.

**East Africa benchmarking**

Rwanda maintained 98% DTP3 coverage in 2024 and had been above 95% for over a decade. Uganda at 91%, Tanzania at 87%. Kenya at 85% was mid-range — better than South Sudan, DRC and Nigeria, below Rwanda, Uganda and Ethiopia (90%). The Rwanda figure, consistent with its performance in the disease surveillance and maternal health analyses, reflected sustained programme investment and community health worker infrastructure rather than resources Kenya could not access.

---

## Charts produced

- `vaccination_national_trend.png` — seven antigen trends 2000–2024 with WHO 90% target line, COVID disruption band and GAVI milestone markers
- `vaccination_dtp3_county.png` — all 46 counties ranked by DTP3 coverage with critical/low/moderate/good category colouring
- `vaccination_antigen_gap.png` — two-panel: 2016 peak vs 2024 current for each antigen; gap to WHO 90% target
- `vaccination_dropout.png` — DTP1 to DTP3 dropout rate trend 2000–2024 — the completion problem alongside the coverage problem
- `vaccination_county_scatter.png` — DTP3 vs MCV1 by county coloured by region, outliers labelled
- `vaccination_regional.png` — East Africa DTP3 comparison 2024, Rwanda benchmark highlighted

---

## Technical approach

```python
# Python stack
pandas · numpy · matplotlib · seaborn · openpyxl · requests

# WHO GHO API connection
import requests

def fetch_immunisation(indicator_code, country='KEN', years=(2000, 2024)):
    url = (f'https://ghoapi.azureedge.net/api/{indicator_code}'
           f'?$filter=SpatialDim eq \'{country}\''
           f' and TimeDim ge {years[0]} and TimeDim le {years[1]}')
    resp = requests.get(url, timeout=30, headers={'Accept': 'application/json'})
    records = resp.json().get('value', [])
    df = pd.DataFrame(records)
    return df.rename(columns={'TimeDim':'Year','NumericValue':'Coverage'})[['Year','Coverage']]

# The 2016 peak confirmation — run this against your df_kenya
peak_val  = df_kenya['DTP3'].max()
peak_year = df_kenya.loc[df_kenya['DTP3'].idxmax(), 'Year']
val_2016  = df_kenya.loc[df_kenya.Year == 2016, 'DTP3'].values[0]

print(f'Peak: {peak_val}% in {peak_year}')
print(f'2016 confirmed: {val_2016}%')
# Output: Peak: 91.0% in 2016 | 2016 confirmed: 91.0%

# Dropout rate calculation
df_kenya['DTP_Dropout_Rate'] = (
    (df_kenya['DTP1'] - df_kenya['DTP3']) / df_kenya['DTP1'] * 100
).round(1)

# County coverage category assignment
def coverage_category(pct):
    if pct < 70:  return 'Critical (<70%)'
    if pct < 80:  return 'Low (70-79%)'
    if pct < 90:  return 'Moderate (80-89%)'
    return 'Good (90%+)'
```

---

## Project structure

```
vaccination-coverage-dashboard/
├── Vaccination_Coverage_EDA.ipynb       # Main analysis notebook
├── Vaccination_Coverage_Dataset.xlsx    # Five-sheet dataset
│   ├── Kenya_National_Trend             # 25 years × 7 antigens
│   ├── Kenya_County_Coverage_2024       # 46-county snapshot
│   ├── East_Africa_Regional_2024        # 10-country comparison
│   ├── Antigen_Gap_Analysis             # Per-antigen peak vs current vs target
│   └── Zero_Dose_Estimates              # Equity layer — unvaccinated children
├── outputs/
│   ├── vaccination_national_trend.png
│   ├── vaccination_dtp3_county.png
│   ├── vaccination_antigen_gap.png
│   ├── vaccination_dropout.png
│   ├── vaccination_county_scatter.png
│   └── vaccination_regional.png
└── README.md
```

---

## Running the notebook

```bash
pip install pandas numpy matplotlib seaborn openpyxl requests
jupyter notebook Vaccination_Coverage_EDA.ipynb
```

The dataset loads from the Excel file. The `fetch_immunisation()` function documented above calls the WHO GHO API live when run on a machine with internet access — no authentication required. The API URL for DTP3 global data:
```
https://ghoapi.azureedge.net/api/WHS8_110
```
Add `?$filter=SpatialDim eq 'KEN'` for Kenya-only data.

---

## Power BI dashboard structure

| Page | Source sheet | Primary visuals |
|:---|:---|:---|
| Executive Overview | Kenya_National_Trend | DTP3 current vs WHO 90% target KPI, 7-antigen trend chart, COVID impact annotation |
| County Coverage Map | Kenya_County_Coverage_2024 | Kenya choropleth by DTP3 category, ranked bar all 46 counties, critical county table |
| Antigen Comparison | Antigen_Gap_Analysis | Peak vs current grouped bar, gap to target horizontal bar, trend direction indicators |
| Dropout Analysis | Kenya_National_Trend | DTP1 to DTP3 dropout rate trend, dropout vs coverage scatter by county |
| Regional Benchmarking | East_Africa_Regional_2024 | East Africa DTP3 comparison bar, Rwanda benchmark annotation, on-track status flags |

---

## Skills this project demonstrates

- **WHO GHO API fluency** — immunisation-specific indicator codes, WUENIC methodology, how to distinguish administrative from survey-based coverage estimates
- **Immunisation programme knowledge** — DTP schedule, dropout rate as a proxy for system completion, GAVI new vaccine introduction timelines, cold chain requirements, zero-dose definition and estimation methodology
- **Kenya health data ecosystem** — KHIS facility reporting, county devolution context, Kenya National Immunisation Policy target framework
- **Equity analysis** — zero-dose children as the equity indicator, geographic clustering of low-coverage counties, connection between immunisation gaps and broader health service utilisation patterns
- **Time series pattern analysis** — peak identification, trend inflection points, COVID disruption quantification, partial recovery assessment

---

## Key definitions

| Term | Definition |
|:---|:---|
| DTP3 | Three doses of diphtheria-tetanus-pertussis vaccine — the primary benchmark for immunisation programme strength |
| MCV1 | First dose of measles-containing vaccine |
| BCG | Bacille Calmette-Guérin — tuberculosis vaccine, typically administered at birth |
| WUENIC | WHO/UNICEF Estimates of National Immunization Coverage — the internationally agreed methodology for national coverage estimation |
| Dropout rate | Proportion of children who received DTP1 but did not complete DTP3 — measures system retention not just access |
| Zero-dose child | A child who received no vaccines at all — the equity benchmark used by GAVI and WHO |
| Herd immunity threshold | The coverage level above which a disease cannot sustain transmission — varies by disease (measles: 95%, polio: 80–85%, diphtheria: 85%) |
| GAVI | Global Alliance for Vaccines and Immunisation — the primary financing mechanism for new vaccine introductions in Kenya |
| Cold chain | Temperature-controlled supply chain required to maintain vaccine efficacy from manufacture to administration |

---

## Data sources

- WHO/UNICEF WUENIC: `who.int/immunization/monitoring_surveillance/data`
- WHO GHO API: `ghoapi.azureedge.net/api`
- Kenya KHIS: `hiskenya.org`
- GAVI Kenya profile: `gavi.org/programmes-impact/country/kenya`
- Kenya National Immunisation Policy 2020–2025: `health.go.ke`

---

**Patience Anono** · PA Data Analytics · [padataanalytics.com](https://padataanalytics.com) · hello@padataanalytics.com · @pa_analytics
