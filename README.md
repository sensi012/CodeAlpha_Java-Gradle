# ☕ CodeAlpha DevOps Internship — Task 3: Java Application using Gradle

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![JUnit](https://img.shields.io/badge/JUnit5-25A162?style=for-the-badge&logo=junit5&logoColor=white)
![CodeAlpha](https://img.shields.io/badge/Internship-CodeAlpha-blue?style=for-the-badge)

---

## 📌 Project Overview

This project demonstrates how to automate the **build, test, and deployment process** of a Java application using **Gradle** as the build automation tool. A **CI/CD pipeline** using GitHub Actions is integrated so that every code push automatically builds and tests the application — following core DevOps principles for Java development.

> **Internship:** CodeAlpha DevOps Internship  
> **Task:** Task 3 — Java Application using Gradle  
> **Intern:** [Adepegba Isaiah]  
> **Duration:** [May] – [June]

---

## 🧠 What I Learned

- What Gradle is and how it replaces manual Java builds
- Managing Java project dependencies using Gradle
- Writing and running **JUnit unit tests** automatically
- Packaging a Java app into a runnable `.jar` file
- Integrating **GitHub Actions** as a CI/CD pipeline for Java
- Understanding how automated builds eliminate human error in delivery

---

## 🏗️ How the Build Pipeline Works

```
Developer writes code & pushes to GitHub
               │
               ▼ (triggers automatically)
        GitHub Actions CI
               │
               ├── Step 1: Set up JDK 17
               │
               ├── Step 2: Run `./gradlew build`
               │              ├── Compile Java source code
               │              ├── Run unit tests (JUnit)
               │              └── Report results
               │
               └── Step 3: Package as .jar file
                              │
                              ▼
                    Build Artifact Ready ✅
```

---

## 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| Java 17 (JDK) | Programming language |
| Gradle | Build automation and dependency management |
| JUnit 5 | Automated unit testing |
| GitHub Actions | CI/CD pipeline execution |
| Git / GitHub | Version control and source hosting |

---

## 📁 Project Structure

```
CodeAlpha_JavaGradle/
├── app/
│   ├── build.gradle                        # Gradle build configuration
│   └── src/
│       ├── main/
│       │   └── java/com/codealpha/
│       │       └── App.java                # Main application code
│       └── test/
│           └── java/com/codealpha/
│               └── AppTest.java            # Unit tests
├── gradle/
│   └── wrapper/
│       └── gradle-wrapper.properties       # Gradle version config
├── .github/
│   └── workflows/
│       └── gradle.yml                      # GitHub Actions CI/CD pipeline
├── gradlew                                 # Unix Gradle wrapper script
├── gradlew.bat                             # Windows Gradle wrapper script
├── settings.gradle                         # Project name settings
└── README.md                               # Project documentation
```

---

## ⚙️ Prerequisites

- [Java JDK 17](https://adoptium.net) — Download and install
- [Gradle](https://gradle.org/install) — Or use the included `gradlew` wrapper (recommended)
- [Git](https://git-scm.com)

Verify your setup:
```bash
java -version      # Should show: openjdk version "17.x.x"
./gradlew --version  # Should show Gradle version
```

---

## 🚀 How to Run This Project

### Step 1 — Clone the Repository
```bash
```

### Step 2 — Build the Project
```bash
./gradlew build
```
This compiles the code, runs tests, and creates a `.jar` file.

### Step 3 — Run the Application
```bash
./gradlew run
```

**Expected Output:**
```
=======================================
Hello from Gradle-built Java app!
=======================================
```

### Step 4 — Run Tests Only
```bash
./gradlew test
```

### Step 5 — Package as JAR
```bash
./gradlew jar
```
The `.jar` file will appear in `app/build/libs/`

### Step 6 — Run the JAR Directly
```bash
java -jar app/build/libs/app.jar
```

---

## 📄 Gradle Build File Explained (build.gradle)

```groovy
plugins {
    id 'java'
    id 'application'
}

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.10.0'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
}

application {
    mainClass = 'com.example.App'
}

test {
    useJUnitPlatform()
}
```

---

## 🤖 CI/CD Pipeline (.github/workflows/gradle.yml)

```yaml
name: Java Gradle CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Set up JDK 17
      uses: actions/setup-java@v4
      with:
        java-version: '17'
        distribution: 'temurin'
    - name: Grant execute permission for gradlew
      run: chmod +x gradlew
    - name: Build with Gradle
      run: ./gradlew build
```

Every push to `main` triggers this pipeline automatically on GitHub.

---

## ✅ Gradle Tasks Reference

| Command | What It Does |
|---------|-------------|
| `./gradlew build` | Compile + test + package |
| `./gradlew run` | Run the application |
| `./gradlew test` | Run unit tests only |
| `./gradlew jar` | Create a `.jar` package |
| `./gradlew clean` | Delete all build files |
| `./gradlew dependencies` | List all project dependencies |

---

## 💡 Key Concepts Demonstrated

- **Build Automation:** `./gradlew build` replaces dozens of manual steps with one command
- **Dependency Management:** Gradle automatically downloads and caches all required libraries
- **Unit Testing:** JUnit tests run automatically on every build to catch bugs early
- **CI/CD Integration:** GitHub Actions runs the build on every push — no manual intervention
- **Artifact Generation:** Gradle packages the app into a portable `.jar` file for deployment

---

## 🔗 Resources

- [Gradle Official Documentation](https://docs.gradle.org)
- [Java at Adoptium (JDK 17)](https://adoptium.net)
- [JUnit 5 Documentation](https://junit.org/junit5/)
- [GitHub Actions for Java](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-java-with-gradle)
- [CodeAlpha Website](https://www.codealpha.tech)

---

## 👤 Author

**[Adepegba Isaiah]**  

*This project was completed as part of the CodeAlpha DevOps Internship Program.*
