# Smart Irrigation & Weather Station

## Project Overview
The **Smart Irrigation & Weather Station** is an IoT-based system designed to monitor environmental parameters such as temperature, humidity, and pressure using the BME280 sensor, while also integrating a security system. This project provides a command and supervision station that collects data, stores it in a MySQL database, and displays it on a web interface. The system uses the ESP32 microcontroller to send data via HTTP POST requests to a web server responsible for data storage and visualization.

## Features
- **Weather Monitoring**: Real-time temperature, humidity, and pressure monitoring using the BME280 sensor.
- **Data Acquisition and Storage**: Sensor data is sent to a MySQL database using HTTP POST.
- **Web Application**: Displays real-time sensor data and historical logs via a user-friendly interface.
- **Responsive Design**: The web interface adapts to different screen sizes (mobile and desktop).
  
## Components
1. **ESP32 Microcontroller**: The device responsible for collecting sensor data and transmitting it to the server.
2. **BME280 Sensor**: Measures temperature, humidity, and pressure.
3. **Database**: MySQL database stores the sensor readings.
4. **Web Application**: Built using PHP, HTML, and CSS for data presentation and interaction.

## Project Files
1. **`esp-database.php`**:  
   - Manages the connection to the MySQL database.
   - Functions to retrieve and store sensor data in the database.
   
2. **`esp-post-data.php`**:  
   - Handles HTTP POST requests sent from the ESP32.
   - Extracts the request's temperature, humidity, and pressure data and stores it in the database.

3. **`esp-style.css`**:  
   - CSS file that defines the styling for the web application, including responsive design and custom gauges for sensor readings.

4. **`esp-weather-station.html`**:  
   - The main web interface that displays the most recent sensor readings, as well as historical data. Users can specify how many historical readings to view. It includes gauges for visualizing temperature and humidity and a table for all readings.

5. **`SensorData_Table.sql`**:  
   - SQL script to create the table `SensorData` in the MySQL database, where sensor readings (temperature, humidity, and pressure) are stored.

## System Architecture
1. **Data Collection**: ESP32 collects temperature, humidity, and pressure data from the BME280 sensor.
2. **Data Transmission**: ESP32 sends sensor data to the server using HTTP POST requests handled by `esp-post-data.php`.
3. **Data Storage**: The PHP script inserts the received data into the MySQL database.
4. **Web Interface**: Users can view real-time and historical data on the `esp-weather-station.html` page, styled by `esp-style.css`. The page uses PHP to fetch data from the database and display it in a user-friendly format.

## Database Setup
To create the MySQL database, use the SQL script provided in `SensorData_Table.sql`:
```sql
CREATE TABLE `SensorData` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `sensor` varchar(20) DEFAULT NULL,
  `location` varchar(50) DEFAULT NULL,
  `value1` float DEFAULT NULL,
  `value2` float DEFAULT NULL,
  `value3` float DEFAULT NULL,
  `reading_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
);
