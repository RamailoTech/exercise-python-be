# Python Backend Developer Task

## Objective

Develop a simple Django application that integrates with a weather API to fetch current weather information for a specified city and logs each search in a database. Enhance the application by offloading long-running or periodic tasks to Celery workers.

## Task Breakdown

### 1. API Integration

- **Weather API:**
  - Use the OpenWeather API (or another similar service) to retrieve weather data.
  - Create a Django view that accepts a city name via a query parameter (e.g., `GET /weather?city={city_name}`) and returns key weather details such as temperature and weather conditions.
  - Implement clear error handling for cases such as invalid city names or API call failures.
  - Implement throttling.

### 2. Search History Storage

- **Database Model:**
  - Create a Django model with the following fields:
    - `city_name` (CharField)
    - `timestamp` (DateTimeField)
  - Every successful weather search should be recorded in the database with the current timestamp.
- **History Endpoint:**
  - Implement a RESTful endpoint `GET /history` that returns the list of past searches (city names and timestamps).

### 3. RESTful API Endpoints

Develop the following endpoints:

- **GET /weather?city={city_name}:**  
  Fetches and returns the weather data for the provided city.
- **GET /history:**  
  Returns the stored search history.

### 4. Celery Integration

Enhance the application with Celery/Celery beat to handle asynchronous tasks and periodic jobs. Use your creativity, examples could be:
- A daily email to an admin email providing statistics of each day.

- **Celery Setup:**
  - Configure Celery within the Django project (e.g., creating a `celery.py` file, setting up the broker such as Redis or RabbitMQ, and ensuring proper integration with Django’s settings).
  - Document the setup and running instructions for Celery in your `README.md`.

### 5. Testing (Optional)

- Write a basic suite of unit tests to verify:
  - The weather endpoint returns correct data and handles errors appropriately.
  - The history endpoint correctly records and returns search history.
  - Celery tasks (both asynchronous and periodic) are correctly queued and executed, with appropriate error handling and retries.

### 6. Documentation

Prepare a `README.md` that includes:

- A brief project description.
- Setup instructions for running the project locally, including:
  - Environment setup (Python 3.8+ and required packages)
  - How to run the Django development server
  - How to start the Celery worker for periodic tasks
- Steps to execute the unit tests.
- API documentation detailing:
  - Available endpoints.
  - Required parameters.
  - Example responses.
- A section on Celery:
  - Description of the asynchronous and periodic tasks.
  - Configuration details for the message broker (e.g., Redis or RabbitMQ).
- Optionally, a section on potential improvements (e.g., adding authentication, caching, or deployment strategies).

## Constraints & Guidelines

- **Language/Version:** Use Python 3.8+.
- **Project Structure:**
  - Organize your project with a clear directory layout, e.g., place tests in a `./tests/` folder.
  - Use a `.gitignore` file to avoid including unnecessary files in the repository.
- **Time Management:**
  - Focus on implementing the core functionalities: fetching weather data, logging search history, and integrating Celery for asynchronous tasks.
  - Document any assumptions or potential improvements in your README.
- **Submission:**
  - Commit your work frequently.
  - Provide the repository link upon submission.
