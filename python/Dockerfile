FROM python:3.7-slim as base

FROM base as builder

# get packages
COPY requirements.txt .
RUN pip install -r requirements.txt

FROM base as final

WORKDIR /pythonserver

# Grab packages from builder
COPY --from=builder /usr/local/lib/python3.7/ /usr/local/lib/python3.7/

# Add the application
COPY . .

EXPOSE 8081
ENTRYPOINT [ "python", "pythonserver.py" ]