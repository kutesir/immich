# immichImmich Self-Hosted Photo & Video Management

This setup runs Immich (a self-hosted photo and video backup solution) using Docker Compose with Redis and PostgreSQL backends, as well as a machine learning service.

Features
	•	Fast media uploads
	•	Machine Learning support for face detection and object recognition
	•	🧩 Redis and PostgreSQL backends
	•	🔁 Automatic container restart on failure
	•	🛡️ Secure Docker settings with no-new-privileges

Requirements
	•	Docker and Docker Compose
	•	Adequate storage and memory (recommend SSD for performance)

Services

immich-server
	•	Exposes UI on port 8212
	•	Upload path bound to /usr/src/app/upload

immich-redis
	•	Caching backend
	•	Stores data under /opt/immich/redis

immich-db
	•	Uses pgvecto-rs image with Postgres 16
	•	Health-checked with pg_isready

immich-machine-learning
	•	Runs AI models (e.g., face detection)
	•	Requires GPU or sufficient CPU

Environment Configuration

All sensitive values and environment variables are in stack.env. Typical values:

POSTGRES_DB=immich
POSTGRES_USER=immichuser
POSTGRES_PASSWORD=immichpw
TZ=Africa/Nairobi

How to Deploy
	1.	Ensure Docker is installed
	2.	Place your stack.env file next to immich.yml
	3.	Run:

docker compose -f immich.yml up -d



Access Immich

Open your browser and go to: http://localhost:8212

Notes
	•	Ensure the volumes and paths used in the docker-compose file are accessible and writable by Docker.
	•	Ports, users, and passwords can be adjusted as needed for your environment.

⸻

🛠 Maintained by [kutesir] for homelab photo/video backup.

