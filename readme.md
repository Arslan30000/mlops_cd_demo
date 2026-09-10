# MLOps Continuous Delivery Demo

A lightweight Machine Learning inference API demonstrating a fully automated Continuous Delivery (CD) pipeline. This project implements strict version control, immutable Docker artifacts, and automated environment promotion using GitHub Actions.

**Pipeline Architecture**
* **Continuous Integration:** Automated linting and testing via Pytest upon commit.
* **Artifact Creation:** Containerizes the Flask application and publishes immutable, semantically versioned images to the GitHub Container Registry (GHCR).
* **Staging Deployment:** Automatically deploys the latest Docker image to a staging environment and executes a health/smoke test validation.
* **Production Deployment:** Pauses for a manual approval gate before promoting the tested artifact to the production environment.

**Tech Stack**
* **Application:** Python 3.12, Flask 3.1.2
* **Testing:** Pytest 8.4.2
* **Containerization:** Docker
* **CI/CD:** GitHub Actions, GitHub Environments, GitHub Container Registry (GHCR)

**Local Setup**
1. Clone the repository and navigate to the directory.
2. Create and activate a virtual environment.
3. Install dependencies:
   `pip install -r requirements.txt`
4. Run tests:
   `python -m pytest`
5. Start the application locally:
   `python app.py`

**Triggering the Pipeline**
The GitHub Actions CD workflow triggers automatically when a semantic version tag is pushed to the repository:
`git tag v1.0.0`
`git push origin v1.0.0`

**API Endpoints**
* `GET /` - Service status check.
* `GET /health` - Returns application health and current model version.
* `POST /predict` - Accepts a JSON payload (`{"value": 5}`) and returns a simulated inference prediction.

**Author**
Muhammad Arslan (23i-0572)  
FAST NUCES, Islamabad