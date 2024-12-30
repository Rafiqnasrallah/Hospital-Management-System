# Hospital Management System

## Overview
The Hospital Management System is a Java-based application designed to streamline patient data management in hospitals. It allows for efficient handling of patient records, classification based on severity, and prioritization of critical cases while tracking deferred patients for future monitoring.

## Features
- **Load Patient Records**: Reads patient data from a text file.
- **Classify Patients**: Automatically categorizes patients into critical (severity ≥ 5) and deferred (severity < 5).
- **Serve Critical Patients**: Processes patients with high severity and calculates treatment costs.
- **Track Deferred Patients**: Stores less critical cases in a stack for later review.
- **Total Treatment Cost**: Computes and displays the total cost of treatment for critical patients.

## Requirements
- **Java JDK 11 or later**
- **Maven** (for building and dependency management)
- **Azure DevOps** (optional for CI/CD pipelines and telemetry integration)

## Project Structure
```
HospitalManagementSystem/
├── src/
│   ├── main/
│   │   └── java/
│   │       ├── Patient.java
│   │       └── HospitalManagementSystem.java
│   └── test/
├── patients.txt
├── README.md
└── pom.xml
```

## How to Run
1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd HospitalManagementSystem
   ```

2. **Compile the Project**:
   ```bash
   mvn compile
   ```

3. **Run the Application**:
   ```bash
   mvn exec:java -Dexec.mainClass="Main"
   ```

4. **Input File**:
   - Ensure `patients.txt` is in the project root and contains patient records in the following format:
     ```
     John Doe 001 NewYork 7
     Jane Smith 002 Chicago 3
     Alice Brown 003 NewYork 5
     Bob Johnson 004 Chicago 8
     ```

5. **Expected Output**:
   ```
   Serving: John Doe (001) - City: NewYork, Severity: 7
   Serving: Alice Brown (003) - City: NewYork, Severity: 5
   Serving: Bob Johnson (004) - City: Chicago, Severity: 8
   Deferred Patients (Stack):
   Jane Smith (002) - City: Chicago, Severity: 3
   Total Treatment Cost: $2000
   ```

## CI/CD Pipeline
1. **Set Up Azure DevOps**:
   - Create a pipeline with the following YAML configuration:
     ```yaml
     trigger:
       branches:
         include:
         - main
     pool:
       vmImage: 'ubuntu-latest'
     steps:
     - task: UseJavaVersion@1
       inputs:
         version: '11'
         architecture: 'x64'
     - script: |
         mvn clean install
       displayName: 'Build and Test'
     ```

2. **Run Tests**:
   - Ensure automated tests validate functionality.

## Contributing
- Fork the repository.
- Create a new branch (`git checkout -b feature-name`).
- Commit changes (`git commit -m "Add feature"`).
- Push to the branch (`git push origin feature-name`).
- Create a pull request.

## License
This project is licensed under the MIT License. See `LICENSE` for more details.

## Contact
For questions or support, contact [Your Name/Email].

