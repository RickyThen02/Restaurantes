# Restaurantes
Crear una WebApp que consulte los restaurantes de Estados Unidos

GET /api/stats

{
  "countries": 20,
  "cities": 2700,
  "restaurants": 25000
}

GET /api/cities

{
  "count": 1234,
  "cities": [
    "Chicago",
    "San Francisco",
    "New York"
  ]
}

GET /api/restaurants

price - Price range for the restaurant. Values: 1-4.
name - Name of the restaurant
address - Address line. Should not contain state or city or zip.
state - State code (ex.: IL)
city - City name (ex.: Chicago)
zip - Zipcode (ex: 60601)
country - Country code (ex: US)
page - Page (default: 1)
per_page - Entries per Page, can be one of [5, 10, 15, 25, 50, 100] (default: 25)

{
  "count": 521,
  "per_page": 25,
  "current_page": 1,
  "restaurants": [ ... ]
}

GET /api/restaurants/:id

{
  "id": 107257,
  "name": "Las Tablas Colombian Steak House",
  "address": "2942 N Lincoln Ave",
  "city": "Chicago",
  "state": "IL",
  "area": "Chicago / Illinois",
  "postal_code": "60657",
  "country": "US",
  "phone": "7738712414",
  "lat": 41.935137,
  "lng": -87.662815,
  "price": 2,
  "reserve_url": "http://www.opentable.com/single.aspx?rid=107257",
  "mobile_reserve_url": "http://mobile.opentable.com/opentable/?restId=107257",
  "image_url": "https://www.opentable.com/img/restimages/107257.jpg"
}


