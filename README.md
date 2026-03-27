# Cloud Storage in Action

A Spring Boot REST API for image management that currently uses local file system storage. The goal of this project is to migrate it to use a **cloud object storage** service, transforming it into a cloud-enabled application.

## About

This project is part of the **Enterprise Cloud Application (ECA)** module in the **Higher Diploma in Software Engineering (HDSE)** program at the **Institute of Software Engineering (IJSE)**. It is intended exclusively for students enrolled in this program.

## Objective

As it stands, this application stores all uploaded images on the local machine (`~/.ijse/eca/storage`). Your task is to **clone this repository** and migrate the storage layer so that it uses a cloud object storage provider (e.g., AWS S3, Google Cloud Storage, Azure Blob Storage), making the application fully cloud-enabled.

## Tech Stack

- Java 25
- Spring Boot 4.0.2
- Maven
- Lombok
- Public Cloud Storage

## API Endpoints

| Method   | Endpoint                    | Description               |
| -------- | --------------------------- | ------------------------- |
| `POST`   | `/api/v1/images`            | Upload an image           |
| `GET`    | `/api/v1/images`            | List all stored images    |
| `GET`    | `/api/v1/images/{filename}` | Retrieve a specific image |
| `DELETE` | `/api/v1/images/{filename}` | Delete a specific image   |

## Getting Started

1. Clone the repository
2. Build the project
   ```bash
   ./mvnw clean install
   ```
3. Run the application
   ```bash
   ./mvnw spring-boot:run
   ```

The application will start on the default port and create the local storage directory at `~/.ijse/eca/storage` if it does not already exist.

## Testing

A Postman collection is available for testing the API endpoints:

[Cloud Storage in Action - Postman Collection](https://www.postman.com/ijse-eca-5768309/workspace/eca-69-70/collection/47280517-cecdea88-0a8b-4f46-b093-4af12ba9ac0d?action=share&creator=47280517)

## Google Service Account JSON (Template)

Do not commit real service account values to GitHub. Keep the real file only on your local machine.

Use this template to understand the expected structure:

```json
{
  "type": "service_account",
  "project_id": "your-gcp-project-id",
  "private_key_id": "your-private-key-id",
  "private_key": "-----BEGIN PRIVATE KEY-----\\nYOUR_PRIVATE_KEY\\n-----END PRIVATE KEY-----\\n",
  "client_email": "your-service-account-email@your-project.iam.gserviceaccount.com",
  "client_id": "your-client-id",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/your-service-account-email%40your-project.iam.gserviceaccount.com",
  "universe_domain": "googleapis.com"
}
```

Setup steps:

1. Download your service account key JSON from Google Cloud Console.
2. Place it in src/main/resources on your local machine.
3. Make sure application.yaml points to that filename in gcp.credentials-location.
4. Keep src/main/resources/\*.json in .gitignore so secrets are never committed.

## Need Help?

If you encounter any issues during the migration, feel free to reach out and start a discussion via the **Slack workspace**.
