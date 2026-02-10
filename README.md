# Python Lab Verifier

Automated coursework verification system. Students fork this repository, implement their assigned tasks, and open Pull Requests to have their work verified automatically via Docker and GitHub Actions.

## Prerequisites

- **Git** installed on your system
- **Docker** installed and running (Ubuntu, macOS, or Windows)

## Repository Structure

Each `submission*/` directory is a self-contained assignment:

| File | Purpose | Student edits? |
|------|---------|:--------------:|
| `main.py` | Your Python solution goes here | Yes |
| `variant.txt` | Your variant number (1-10) | Yes |
| `verify.sh` | Verification script (runs tests for your variant) | No |
| `Dockerfile` | Docker build configuration | No |
| `README.md` | Assignment-specific instructions | No |

More `submission*/` directories will be added over the course of the semester.

## Student Workflow

### 1. Fork and clone

Fork this repository on GitHub, then clone your fork:

```bash
git clone https://github.com/<your-username>/basics_of_python.git
cd basics_of_python
```

### 2. Set your variant

Write your variant number (1-10) into the `variant.txt` file of the submission you are working on:

```bash
echo "1" > submission1/variant.txt
```

### 3. Implement your solution

Open `submission1/main.py` and implement the task described in `submission1/README.md` for your variant.

### 4. Test locally with Docker

Build and run the verification container:

```bash
docker build -t submission1 submission1/
docker run --rm submission1
```

A passing submission prints `PASS` and exits with code 0. A failing submission prints `FAIL` and exits with a non-zero code.

### 5. Open a Pull Request

Push your changes to your fork and open a Pull Request back to the original repository. GitHub Actions will automatically run the verification and show a green check (pass) or red X (fail) on your PR.
