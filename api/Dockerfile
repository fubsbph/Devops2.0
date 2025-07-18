FROM python:3.9

# Set the working directory in the container
WORKDIR /usr/src/app
# Copy the requirements file into the container
COPY requirements.txt ./
# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt
# Copy the rest of the application code into the container
COPY . .
# Expose the port the app runs on
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]