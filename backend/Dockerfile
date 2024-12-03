# Specify the base image
FROM python:3.12-slim

# Create the working directory
WORKDIR /backend

# Copy the backend code to the working directory, and install the dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the backend code to the working directory
COPY . .

# Expose port 5000 for the backend
EXPOSE 5000

# Start the Flask Dev Server when the container launches
CMD ["python3", "app.py"]