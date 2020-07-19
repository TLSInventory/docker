# Docker deployment of TLSInventory

You can deploy your own instance of TLSInventory using the following steps or use existing public instance [tlsinventory.com](https://tlsinventory.com).

## Docker deployment

Install using
```bash
# git clone https://github.com/BorysekOndrej/bakalarka-general.git
git clone https://github.com/TLSInventory/Docker.git
cd Docker/config
cp backend/dist.env backend/.env
cp frontend/dist.env frontend/.env
cp sslyze_rq/dist.env sslyze_rq/.env

# Manual steps:
# Replace all config values, which are uncommented and contain value FILL_MANUALY

# For backend/.env thats: (double commented values are optional)

# SERVER_PUBLIC_URL=FILL_MANUALLY
# JWT_SECRET_KEY=FILL_MANUALLY_AT_LEAST_90_CHARS
# # SLACK_API_TOKEN=xoxb-FILL_MANUALLY
# # SLACK_CLIENT_ID=FILL_MANUALLY
# # SLACK_CLIENT_SECRET=FILL_MANUALLY
# SENSOR_COLLECTOR_KEY=FILL_MANUALLY


# For sslyze_rq/.env it is:
# SENSOR_COLLECTOR_KEY=FILL_MANUALLY

# For nginx/nginx.conf it is:
# server_name            FILL_MANUALLY


# Then run:
# docker-compose up --build -d
```

Update using:
```bash
docker-compose pull
docker-compose up --build -d # --remove-orphans
# docker image prune  # Optional: This removes all dangling images. Not just the ones from this project.
```
