# OpenCut (Containerized)

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.com/deploy/opencut?referralCode=rees)

A containerized version of [OpenCut](https://github.com/OpenCut-app/opencut-classic) - the free, open-source video editor. This template is designed for easy deployment on Railway, but can run anywhere Docker is supported.

## What is OpenCut?

OpenCut is a privacy-focused, browser-based video editor that keeps your videos on your device. No watermarks, no subscriptions, just free video editing.

**Features:**
- Timeline-based editing
- Multi-track support  
- Real-time preview
- Client-side processing (files never leave your browser)
- No watermarks or subscriptions

## What This Template Provides

This fork makes a few key modifications to the original OpenCut project to enable easy deployment in a containerized environment:

1. **Auth Configuration** - Runtime environment variable handling for the site URL used by auth
2. **Migration Support** - Added Drizzle migration files and dependencies to Docker image  
3. **Build Optimization** - Configured standalone Next.js build for containerization

## Quick Deploy

Click the button above or use this template URL:
```
https://railway.com/deploy/opencut?referralCode=rees
```

Railway will automatically:
1. Create a PostgreSQL database
2. Run database migrations
3. Deploy the containerized application
4. Provide you with a public URL

## Environment Variables

The template configures these automatically, but for reference:

| Variable | Description | Default |
|----------|-------------|---------|
| `DATABASE_URL` | PostgreSQL connection string | *Set by Railway* |
| `NEXT_PUBLIC_SITE_URL` | Base URL for the site and authentication | *Your Railway domain* |
| `BETTER_AUTH_SECRET` | Auth encryption secret | *Generated randomly* |
| `UPSTASH_REDIS_REST_URL` | Redis connection URL | *Set by Railway* |
| `UPSTASH_REDIS_REST_TOKEN` | Redis auth token | *Set by Railway* |
| `NEXT_PUBLIC_MARBLE_API_URL` | Marble CMS API URL (blog) | `https://api.marblecms.com` |
| `MARBLE_WORKSPACE_KEY` | Marble CMS workspace key (blog) | *Required, any value if unused* |
| `FREESOUND_CLIENT_ID` | Freesound client ID (sound library) | *Required, any value if unused* |
| `FREESOUND_API_KEY` | Freesound API key (sound library) | *Required, any value if unused* |

## Local Development

To run this containerized version locally:

```bash
# Clone this repository
git clone https://github.com/ReesMorris/OpenCut.git
cd OpenCut

# Build the Docker image
docker build -t opencut -f apps/web/Dockerfile .

# Run with environment variables
docker run -p 3000:3000 \
  -e NEXT_PUBLIC_SITE_URL=http://localhost:3000 \
  -e BETTER_AUTH_SECRET=your-secret-here \
  -e DATABASE_URL=your-db-url \
  -e UPSTASH_REDIS_REST_URL=your-redis-url \
  -e UPSTASH_REDIS_REST_TOKEN=your-redis-token \
  -e NEXT_PUBLIC_MARBLE_API_URL=https://api.marblecms.com \
  -e MARBLE_WORKSPACE_KEY=unused \
  -e FREESOUND_CLIENT_ID=unused \
  -e FREESOUND_API_KEY=unused \
  opencut
```

## Upstream Sync

This template tracks [OpenCut-app/opencut-classic](https://github.com/OpenCut-app/opencut-classic), the original version of OpenCut. Upstream has archived it while [OpenCut-app/OpenCut](https://github.com/OpenCut-app/OpenCut) is rewritten from the ground up, so it receives no further updates. This template will keep deploying the classic editor until the rewrite is ready.

## Support

- **Template Issues:** Post on the [template discussion board](https://station.railway.com/templates/open-cut-01b73deb)
- **OpenCut Issues:** Report to the [main OpenCut repository](https://github.com/OpenCut-app/OpenCut/issues)
- **Railway Issues:** Check [Railway's documentation](https://docs.railway.app/)

## License

This project maintains the same [MIT License](LICENSE) as the original OpenCut project.