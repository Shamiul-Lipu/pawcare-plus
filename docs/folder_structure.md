pawcare-plus/
│
├── client/ # React Frontend
│ ├── public/
│ ├── src/
│ │ ├── components/
│ │ ├── layouts/
│ │ ├── hooks/
│ │ ├── utils/
│ │ ├── context/
│ │ ├── services/ # API functions
│ │ ├── pages/ # React Router/Next pages
│ │ ├── features/ # Modular architecture
│ │ │ ├── marketplace/
│ │ │ ├── cart/
│ │ │ ├── orders/
│ │ │ ├── wishlist/
│ │ │ ├── vets/
│ │ │ ├── appointments/
│ │ │ ├── pets/
│ │ │ ├── ai/
│ │ │ ├── lostFound/
│ │ │ ├── shelters/
│ │ │ └── dashboards/
│ │ └── index.js
│ ├── .env.development
│ ├── .env.production
│ └── package.json
│
├── server/ # Node/Express Backend
│ ├── src/
│ │ ├── config/
│ │ │ ├── db.js
│ │ │ ├── env.js
│ │ │ └── logger.js
│ │ ├── modules/ # Modular Feature-Based Backend
│ │ │ ├── auth/
│ │ │ ├── users/
│ │ │ ├── products/
│ │ │ ├── reviews/
│ │ │ ├── cart/
│ │ │ ├── orders/
│ │ │ ├── wishlist/
│ │ │ ├── vets/
│ │ │ ├── appointments/
│ │ │ ├── pets/
│ │ │ ├── medicalRecords/
│ │ │ ├── ai/
│ │ │ ├── lostFound/
│ │ │ ├── shelters/
│ │ │ └── dashboards/
│ │ ├── utils/
│ │ ├── middleware/
│ │ ├── jobs/ # Cron jobs (reminders, notifications)
│ │ ├── services/ # Shared service logic
│ │ ├── app.js
│ │ └── server.js
│ ├── .env.development
│ ├── .env.production
│ ├── Dockerfile
│ └── package.json
│
├── shared/ # Shared TS types, utilities
│ ├── types/
│ └── constants/
│
├── infra/ # DevOps / Deployment
│ ├── docker/
│ │ ├── client.Dockerfile
│ │ ├── server.Dockerfile
│ ├── docker-compose.dev.yml
│ ├── docker-compose.prod.yml
│ ├── nginx/
│ ├── terraform/
│ └── k8s/
│
├── scripts/ # Automation scripts
│ ├── seed.js
│ ├── build-all.sh
│ └── deploy.sh
│
├── docs/ # Full documentation
│ ├── api/
│ ├── db-schema/
│ ├── feature-requirements.md
│ ├── architecture.md
│ └── workflows.md
│
├── .github/
│ └── workflows/
│ ├── test.yml
│ ├── build.yml
│ └── deploy.yml
│
├── package.json # Root - workspace manager
├── pnpm-workspace.yaml
└── README.md
