Vahan Bazar — Two-Wheeler Marketplace & Dealer Platform

Repo/Project Title: vahan-bazar
Team: Team Name • Member1 • Member2 • Member3 • Member4
Round: 1 • Branch: r1-prototype
Video Pitch: Google Drive link (Anyone with link can view)

1) Project Summary

Problem Understanding: (2–4 lines)

Proposed Prototype Solution: (4–6 lines)

Uniqueness & Impact: (2–4 lines)

2) Core Features (Round-1 Scope)

Listings (image, name, price), Search & Filters (brand, price, fuel, mileage)

Product Page: specs, images, price, offers

Compare up to 4 models side-by-side

Calculators: EMI & Fuel/Charging cost

Used Bikes: browse + submit listing form

Showrooms: directory & Test-Ride booking

Upcoming Launches with dates

Optional (if time permits): Login + Favorites, Reviews/Ratings, Price Alerts, Dealer Dashboard (basic), Recommendations

3) Tech Stack

Frontend: React (Vite, React Router), Tailwind, Zustand (state), Axios

Backend: Node.js (Express), Prisma ORM

DB: PostgreSQL (SQLite for dev)

Auth: JWT (future), OAuth (future)

Deploy (future): Docker + Render/Fly.io + NeonDB

4) Architecture (High-level)

React SPA → REST API (Express) → PostgreSQL

Services: Vehicles, Specs, Media, Dealers, Bookings, Users, Reviews, Alerts

5) Data Model (key tables)

users(id, name, email, phone, role)

vehicles(id, brand, model, type[bike/scooter], fuel[petrol/ev], price_ex_showroom, mileage_kmpl, battery_capacity_kwh, range_km, power_bhp, torque_nm)

vehicle_images(id, vehicle_id, url)

dealers(id, name, city, lat, lng, phone) • showrooms(id, dealer_id, address)

test_rides(id, user_id, vehicle_id, showroom_id, slot_time, status)

used_listings(id, seller_user_id, title, make, model, year, odo_km, price, city, status)

reviews(id, user_id, vehicle_id, rating, comment)

price_alerts(id, user_id, vehicle_id, target_price)

upcoming_launches(id, vehicle_id/null, title, launch_date, expected_price)

6) API (sample)

GET /api/vehicles?brand=&fuel=&price_min=&price_max=&q=

GET /api/vehicles/:id

POST /api/compare (body: [ids])

POST /api/calc/emi (principal, rate_pa, months)

POST /api/calc/fuel (distance_pm, mileage_kmpl OR efficiency_km_per_kwh, fuel_price)

GET /api/showrooms?city= • POST /api/test-rides

GET /api/used • POST /api/used

GET /api/upcoming

7) Calculators (formulas)

EMI: EMI = P * r * (1+r)^n / ((1+r)^n - 1) where r = annual_rate/12/100, n = months

Fuel Cost (ICE): monthly_cost = (distance_pm / mileage_kmpl) * fuel_price

Charging Cost (EV): monthly_cost = (distance_pm / efficiency_km_per_kwh) * electricity_price_per_kwh
