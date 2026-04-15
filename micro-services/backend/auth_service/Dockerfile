FROM python:3.9-slim
WORKDIR /app

# 1. Path to requirements (standing in micro-services, go into backend/auth_service)
COPY backend/auth_service/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 2. Path to common (standing in micro-services, go into backend/common)
COPY ./backend/common ./common

# 3. Path to src (standing in micro-services, go into backend/auth_service/src)
COPY ./backend/auth_service/src ./src

# 4. Tell Python where the root is so 'import common' works
ENV PYTHONPATH=/app

# 5. Start the engine
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]