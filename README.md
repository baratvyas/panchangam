# Standalone Panchangam Web Application

This is a fully client-side, standalone web application that dynamically calculates and displays the daily Hindu lunar calendar, known as the Panchangam. It requires no backend server and can be run directly in any modern web browser by opening the `index.html` file.

## Features

* **Fully Dynamic:** Calculates all core Panchangam elements for the user's current date and time.
* **No Backend Required:** All calculations are performed on the client-side using JavaScript, making it lightweight and easy to host.
* **Multilingual Support:** Displays all information in three different scripts:
    * **English** (IAST Transliteration)
    * **Devanagari** (for Hindi/Sanskrit)
    * **Telugu**
* **Transition Timings:** Calculates and displays the precise end times for `Tithiḥ`, `Nakṣatram`, `Yogaḥ`, and `Karaṇam`, showing which element will come next.
* **Responsive Design:** A clean, modern UI built with Tailwind CSS that works well on both desktop and mobile devices.
* **Easy to Host:** As a single `index.html` file, it can be easily deployed on static hosting services like GitHub Pages, Netlify, or Vercel.

## How It Works

The application uses a self-contained JavaScript engine to perform all astronomical calculations.

1.  **Astronomical Engine (Simulated):** The core logic resides within the `<script>` tag in `index.html`. It includes functions that simulate a professional ephemeris library:
    * `getApproxLongitude(date)`: Calculates the approximate longitude of the Sun and Moon for any given date. This is the foundation for all other calculations.
    * `calculateTithiDetails(date)`, `calculateNakshatramDetails(date)`, etc.: These functions use the solar and lunar longitudes to derive the corresponding Panchangam element and its exact end time.

2.  **Data Structures:** Multilingual names for all elements are stored in comprehensive JavaScript objects (`LABELS`, `TITHI_NAMES`, `NAKSHATRA_NAMES`, etc.), making it easy to manage and extend the language support.

3.  **Dynamic Rendering:** On page load, the main `renderPanchangam()` function:
    * Gets the user's current date and time.
    * Calls all the calculation functions to get the day's Panchangam data.
    * Dynamically builds the HTML list items for each language tab, populating them with the correct labels and values.

## How to Use

Simply open the `index.html` file in a web browser like Chrome, Firefox, or Safari. The application will automatically calculate and display the Panchangam for the current day.

To host it online, you can:

1.  Create a new repository on GitHub.
2.  Upload the `index.html` file to the repository.
3.  Go to the repository's **Settings > Pages**.
4.  Select the `main` branch as the source and click **Save**. Your application will be live at `https://<your-username>.github.io/<repository-name>/`.

## Future Improvements

* **Use a Professional Ephemeris Library:** For even greater accuracy, the simulated calculation functions could be replaced with calls to a professional WebAssembly-based library like the Swiss Ephemeris.
* **Location Services:** Implement geolocation to automatically detect the user's location and calculate the Panchangam for their specific timezone and coordinates, rather than defaulting to Dublin.
* **Sankalpam Generator:** Add a feature to generate the full Sankalpam text based on the calculated data and user-provided Gotra/Nama.