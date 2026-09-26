# Data: Hotel Booking Demand
 
`hotel_bookings.csv` has 119,390 rows and 32 columns. Each row is one booking at one of two hotels in Portugal (H1 is a resort in the Algarve, H2 is a city hotel in Lisbon), with arrivals between July 2015 and August 2017.
 
**Original source:** Antonio, N., Almeida, A. & Nunes, L. (2019). *Hotel booking demand datasets.* Data in Brief, 22, 41–49. https://doi.org/10.1016/j.dib.2018.11.126. Also available on Kaggle.
 
| Column | Description |
|---|---|
| `hotel` | Resort Hotel or City Hotel |
| `is_canceled` | 1 = cancelled, 0 = not cancelled |
| `lead_time` | Days between booking and arrival |
| `arrival_date_year` / `_month` / `_week_number` / `_day_of_month` | Arrival date |
| `stays_in_weekend_nights` / `stays_in_week_nights` | Nights booked |
| `adults`, `children`, `babies` | Guest counts |
| `meal` | BB = Bed & Breakfast, HB = Half Board, FB = Full Board, SC/Undefined = no meal |
| `country` | Guest country of origin (ISO 3166-1 alpha-3) |
| `market_segment`, `distribution_channel` | e.g. Online TA, Offline TA/TO, Direct, Corporate, Groups |
| `is_repeated_guest` | 1 = returning guest |
| `previous_cancellations`, `previous_bookings_not_canceled` | Guest history |
| `reserved_room_type`, `assigned_room_type` | Room codes (anonymised) |
| `booking_changes` | Number of changes before check-in or cancellation |
| `deposit_type` | No Deposit, Non Refund, Refundable |
| `agent`, `company` | Anonymised IDs of the booking agent or company |
| `days_in_waiting_list` | Days before the booking was confirmed |
| `customer_type` | Transient, Transient-Party, Contract, Group |
| `adr` | Average Daily Rate (€) = lodging revenue ÷ nights |
| `required_car_parking_spaces`, `total_of_special_requests` | Extra requests |
| `reservation_status`, `reservation_status_date` | Check-Out, Canceled or No-Show, and the date it was set |
 
**Cleaning applied in Tableau:** `children` NULL → 0; `country` NULL → "Unknown"; meal codes mapped to readable labels.
