# maven-bintray-publish.gradle v0.0.1

My own version of publishing setting script for `maven` and `bintray`, inspired by [gradle-mvn-push](https://github.com/chrisbanes/gradle-mvn-push).

# Usage

### 1. Download script

```sh
wget https://raw.githubusercontent.com/kt3k/maven-bintray-publish.gradle/v0.0.1/maven-bintray-publish.gradle
```

### 2. Add values to `gradle.properties`

An example of home local gradle.properties (for sensitive data):

```properties
signing.keyId=ABCD1234
signing.password=t3k1t0
signing.secretKeyRingFile=~/.gnupg/secring.gpg

sonatype.username=example-user
sonatype.password=n4n1k4

bintray.username=example-user
bintray.apiKey=86f7e437faa5a7fce15Oooocb9eaeaea377667b8
```

An example of project gradle.properties:
```properties
version=1.2.3
group=org.example.library

pom.name=Example Library
pom.description=This is an example description
pom.url=http://example.org/library

pom.scm.url=scm:git@example.org/library.git
pom.scm.connection=scm:git@example.org/library.git
pom.scm.developer.connection=scm:git@example.org/library.git

pom.license.name=MIT
pom.license.url=http://example.org/library/LICENSE
pom.license.distribution=repo

pom.developer.id=example
pom.developer.name=Jean Dupont

bintray.name=example-library
bintray.repo=maven
```

### 3. Apply script

In `build.gradle`:

```groovy
apply from: 'path/to/maven-bintray-publish.gradle'

buildscript {
    repositories {
        jcenter()
    }

    dependencies {
        classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:0.5'
    }
}
```

### 4. Publish

```sh
./gradlew uploadArchives # maven release
./gradlew bintray # bintray
```
