# Stage 1: Use an official Python runtime as a parent image
# Using a 'slim' variant is a good practice for smaller image sizes.
FROM python:3.11-slim

# Stage 2: Set the working directory in the container
WORKDIR /app

# Stage 3: Copy the dependencies file and install them
# This is done in a separate step to leverage Docker's layer caching.
# If requirements.txt doesn't change, this layer won't be rebuilt.
COPY requirements.txt .

# Install dependencies
# --no-cache-dir: Disables the pip cache to keep the image lean.
# --upgrade pip: Good practice to ensure pip is up to date.
RUN pip install --no-cache-dir --upgrade pip -r requirements.txt

# Stage 4: Copy the rest of the application's code
COPY . .

# Stage 5: Expose the port the app runs on
EXPOSE 8000

# Stage 6: Define the command to run the app when the container starts
# Use 0.0.0.0 to make the server accessible from outside the container.
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
