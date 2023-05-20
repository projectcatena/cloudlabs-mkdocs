# Getting started

The front-end component of CloudLabs is built using Next.js, and TailwindCSS. Prebuilt components from Preline was also used in the project.  

GitHub repository: [cloudlabs/app](https://github.com/projectcatena/cloudlabs-app)

## Setup

The project may be deployed locally using npm:
```bash
# Install dependencies
npm install

# Run development server
npm run dev
```

Alternatively, docker/podman may be used:
```bash
# Build image
docker build -t cloudlabs/app .

# Run as container
docker run -p 3000:3000 cloudlabs/app
```

After which, head on to `http://localhost:3000` to see the live website.

<!-- ## Project Layout -->