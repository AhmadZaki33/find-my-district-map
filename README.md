### Find My District Map

The "Find My District Map" web page helps users locate their council district based on their address. It uses Leaflet.js to display an interactive map, jQuery for handling user input and API calls, and Turf.js for geospatial analysis.

#### HTML Structure
- **Head Section**: 
  - Includes necessary meta tags, stylesheet links (Leaflet and Bootstrap), and script links (Leaflet, jQuery, and Turf.js).
  - Defines the style for the map and other elements.
- **Body Section**:
  - Contains a header with a link to the NYC Council districts page.
  - Contains an input form for users to enter their address.
  - Contains a div to display the map.

#### JavaScript Functionality
- **Initialization**:
  - The map is initialized and centered on New York City using Leaflet.js.
  - A tile layer is added to the map from CartoDB's basemaps.
  - Council district boundaries are fetched and displayed as a GeoJSON layer with district numbers.

- **Address Autocomplete**:
  - Listens for user input in the address input field.
  - Fetches address suggestions using the Planning Labs NYC GeoSearch API and displays them in a dropdown list.

- **Address Selection**:
  - When a user selects an address, it fetches the coordinates and address details from the GeoSearch API.
  - Checks which council district the address falls into using the SODA API and Turf.js.
  - Displays the selected address and council district information on the map with a marker and popup.

### API Usage
- **GeoSearch API (Planning Labs NYC)**:
  - Provides address suggestions and search results based on user input.
  - Endpoints:
    - Autocomplete: `https://geosearch.planninglabs.nyc/v2/autocomplete?text={query}`
    - Search: `https://geosearch.planninglabs.nyc/v2/search?text={address}`

- **NYC Council Districts GeoJSON (ArcGIS)**:
  - Fetches the GeoJSON data for the council district boundaries.
  - Endpoint: `https://services5.arcgis.com/GfwWNkhOj9bNBqoJ/arcgis/rest/services/NYC_City_Council_Districts/FeatureServer/0/query?where=1%3D1&outFields=*&outSR=4326&f=geojson`

- **SODA API (NYC Open Data)**:
  - Provides detailed information about council districts.
  - Endpoint: `https://data.cityofnewyork.us/resource/s2hu-y8ab.json`

### Methods and Functions
- **jQuery**:
  - Handles user input and API calls.
  - Updates the DOM with address suggestions and selected address details.
  
- **Leaflet.js**:
  - Initializes and manages the interactive map.
  - Adds and styles map layers and markers.
  - Binds popups to markers.

- **Turf.js**:
  - Performs geospatial analysis to check if a point falls within a specific council district polygon.