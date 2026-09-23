# Back-End-Development-Songs

A Flask microservice that serves song lyrics for the band website. The service
stores songs in a MongoDB database and exposes a RESTful API for listing,
creating, reading, updating, and deleting song resources, accessed through
[PyMongo](https://pymongo.readthedocs.io/).

## REST API Endpoints

| Action | Method | Return code     | Body                       | URL Endpoint   |
|--------|--------|------------------|-----------------------------|----------------|
| List   | GET    | 200 OK           | Array of songs `[{...}]`    | `/song`        |
| Create | POST   | 201 CREATED      | A song resource as json `{...}` | `/song`   |
| Read   | GET    | 200 OK           | A song as json `{...}`      | `/song/{id}`   |
| Update | PUT    | 200 OK           | A song as json `{...}`      | `/song/{id}`   |
| Delete | DELETE | 204 NO CONTENT   | `""`                         | `/song/{id}`   |
| Health | GET    | 200 OK           | `""`                         | `/health`      |
| Count  | GET    | 200 OK           | `""`                         | `/count`       |

## Environment Setup

This repository was created from the `nyu-devops/lab-flask-tdd` template and
configured as follows:

1. Clone this repository and change into its directory:

   ```bash
   git clone https://github.com/sofirij/Back-End-Development-Songs.git
   cd Back-End-Development-Songs
   ```

2. Run the environment setup script:

   ```bash
   bin/setup.sh
   ```

   This installs Python 3.9.x, creates a Python virtual environment named
   `backend-songs-venv`, and installs all of the project dependencies. The
   script completed successfully, and the developer environment was
   verified with:

   ```bash
   python3.9 --version
   # Python 3.9.x
   ```

3. Exit and reopen the terminal (or run `exit`) so that the new shell
   activates the `backend-songs-venv` virtual environment automatically.

## Local Setup

1. Activate the virtual environment (if not already active):

   ```bash
   source ~/backend-songs-venv/bin/activate
   ```

2. Install dependencies (already handled by `bin/setup.sh`, but can be
   re-run manually):

   ```bash
   pip install -r requirements.txt
   ```

3. Start a MongoDB server and export its connection details, then run the
   Flask app:

   ```bash
   MONGODB_SERVICE=localhost MONGODB_USERNAME=root MONGODB_PASSWORD=password flask run
   ```

   The service starts on `http://localhost:5000` by default.

## Running Tests

```bash
pytest
```

## License

Licensed under the [Apache License 2.0](LICENSE).
