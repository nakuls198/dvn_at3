# Hotel Booking Insights Dashboard (Tableau)
 
**An interactive Tableau dashboard that analyses 119,390 hotel bookings to help hotel managers grow revenue, cut cancellations and plan for peak periods.**
 
[![Dashboard overview](images/dashboard-overview.png)](https://public.tableau.com/app/profile/yamuna.g.c/viz/DVN_HotelBookings/Dashboard1)
 
🔗 **[Explore the live dashboard on Tableau Public](https://public.tableau.com/app/profile/yamuna.g.c/viz/DVN_HotelBookings/Dashboard1)**
 
`Tableau` `Data Visualisation` `Data Storytelling` `Dashboard Design` `KPI Design` `Business Analytics`
 
---
 
## Business problem
 
Hotel bookings spike without warning, and more than a third of reservations are cancelled. Revenue managers need a single view that shows **when** demand peaks, **who** their most valuable guests are and **which** bookings are likely to fall through.
 
**Audience:** hotel managers and revenue and operations teams.
 
**Questions answered**
 
1. When are the busiest months, and how do resort and city hotels differ?
2. Do demanding guests (those with more special requests) pay more or cancel more?
3. Which customer type pays more and cancels less, giving "guaranteed" revenue?
4. Which customer types are most likely to cancel?
5. How long does each type of guest stay?
## Data
 
| | |
|---|---|
| **Source** | Hotel Bookings dataset on Kaggle, originally from [Antonio, Almeida & Nunes (2019), *Hotel booking demand datasets*, Data in Brief](https://doi.org/10.1016/j.dib.2018.11.126) |
| **Size** | 119,390 bookings × 32 columns, arrivals from Jul 2015 to Aug 2017 |
| **Hotels** | Resort Hotel (Algarve) and City Hotel (Lisbon), Portugal |
| **Fields** | lead time, arrival dates, stay length, guest mix, country, market segment, customer type, deposit type, ADR (average daily rate, €), special requests, cancellation status |
 
See [`data/README.md`](data/README.md) for the column descriptions.
 
## Dashboard design
 
The workbook has **4 dashboards and 25 worksheets**. Each dashboard answers one manager question, and all of them are driven by a **Select Year** parameter.
 
| Dashboard | Question it answers | What's on it |
|---|---|---|
| **1. Overview** | "How is the business tracking?" | Total bookings with a year-on-year ▲/▼ indicator, monthly bookings by hotel, monthly price changes, a booking map by country, lead time vs cancellation |
| **2. Spot Revenue Opportunities** | "Where is the money?" | KPIs for average ADR, peak ADR month and most profitable segment; ADR by market segment; ADR vs lead time; customer type vs ADR and cancellation; special requests vs ADR |
| **3. Mitigate Risks** | "What is costing us?" | KPIs for total bookings, cancellations, revenue and **revenue lost to cancellations**; cancellation rate over time; by deposit type; by customer type; special requests vs cancellations and booking changes |
| **4. Know Your Guests** | "Who are our guests?" | KPIs for loyal-customer % and special requests per booking; guest mix by season and hotel; popular room and meal combinations; average stay by customer type |
 
**Design choices**
 
- The KPI cards sit across the top of each dashboard so the key numbers can be read in about five seconds.
- Colours are consistent throughout: **red for cancellations and risk**, **green for revenue**.
- Each chart title is written as a question the manager would ask ("Do guests cancel less when they pay upfront?").
- There are few clicks: one year parameter controls all the KPIs.
**Key calculated fields**
 
```
Revenue Per Booking  = [adr] * ([stays_in_week_nights] + [stays_in_weekend_nights])
Lost Revenue         = IF [is_canceled] = 1 THEN [adr] * (total nights) ELSE 0 END
Cancellation Rate    = AVG(IF [is_canceled] = 1 THEN 1 ELSE 0 END)
% Change in Bookings = (Current Year Bookings - Prior Year Bookings) / Prior Year Bookings
Change Tag           = IF [% Change] > 0 THEN "▲" ELSEIF [% Change] < 0 THEN "▼" END
Repeat Guest Rate    = AVG([is_repeated_guest])
Meal Ordered         = CASE [meal] WHEN 'BB' THEN 'Bed & Breakfast' WHEN 'HB' THEN 'Half Board' ... END
```
 
**Data cleaning:** null `children` values were set to 0, null `country` values were set to "Unknown", and meal codes were mapped to readable labels.
 
## Key insights
 
> Revenue figures are estimates (ADR × nights), in €.
 
1. **Cancellations are the biggest leak.** 37% of all bookings were cancelled (City Hotel 42%, Resort Hotel 28%). That represents about **€16.7M of estimated revenue, around 39% of booked value**.
2. **Early bookers are the riskiest.** The cancellation rate rises steadily with lead time, from **10% for bookings made within a week of arrival to 68% for bookings made more than a year out**.
3. **Non-refundable deposits don't stop cancellations.** 99% of non-refundable bookings were cancelled, against 28% with no deposit. This points to a data or process issue (for example, bulk agency blocks) worth investigating rather than a policy that works.
4. **Demanding guests are the best guests.** Guests with no special requests cancel 48% of the time. With one or more requests this falls to **22% or lower**, and ADR rises from about €95 to €124–131.
5. **Transient guests pay most but are the least reliable.** Transient guests have the highest ADR (about €107) and also the highest cancellation rate (41%). **Group** bookings cancel only 10%, and Transient-Party bookings 25%, which makes them the more "guaranteed" revenue.
6. **Summer drives demand and price.** July and August are the busiest months at both hotels. The Resort Hotel's ADR jumps to **about €187 in August**, compared with about €115 at the City Hotel.
7. **Online travel agents dominate high-value demand.** The Online TA segment has the highest average ADR (about €117), just ahead of Direct bookings (about €115).
8. **Loyalty is untapped.** Only 3.2% of guests are repeat guests, a clear opportunity for a loyalty programme.
## Recommendations for hotel managers
 
- Add **tiered deposits or reconfirmation** for bookings made more than 90 days ahead.
- **Target groups and Transient-Party** customers for more reliable base occupancy.
- **Invite special requests at booking time**, because engaged guests cancel less and pay more.
- **Raise resort prices and set minimum stays** in July and August, and run promotions in the off-season.
- Launch a **loyalty or direct-booking incentive** to lift the 3% repeat rate and reduce OTA commissions.
## Repository contents
 
```
hotel-bookings-tableau-dashboard/
├── README.md
├── dashboard/DVN_Hotel_Bookings.twbx      # packaged Tableau workbook (opens in Tableau Desktop / Reader)
├── presentation/Hotel_Booking_Insights.pdf
├── images/                                # dashboard screenshots
└── data/
    ├── hotel_bookings.csv
    └── README.md
```
 
**To open it:** download the `.twbx` file and open it in [Tableau Desktop](https://www.tableau.com/products/desktop) or the free [Tableau Reader](https://www.tableau.com/products/reader). Or use the Tableau Public link above.
 
## Team
 
This was a group project (Group 27) with Tony Xie, Ananya Srinivas, Yamuna G C, Adrian Mato and Nakul Sidiginamola.
 
 
---
 
*Subject 36104 Data Visualisation and Narratives, Master of Data Science and Innovation, University of Technology Sydney (Autumn 2025).*
