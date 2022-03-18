# Reproduction for Gradle Project in Renovate

This project uses gradle and demonstrates that the `repositories` block in build.gradle with a custom repo specified is being ignored by Renovate. Here are the logs from Renovate's run of this project (self-hosted docker, repo in bitbucket)

    March 18th 2022, 16:00:17.247	Found gradle-wrapper package files	rp/renovate-repro
    March 18th 2022, 16:00:17.247	Found 3 package file(s)	rp/renovate-repro
    March 18th 2022, 16:00:17.247	Dependency extraction complete	rp/renovate-repro
    March 18th 2022, 16:00:17.247	Looking up org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://repo.maven.apache.org/maven2/	rp/renovate-repro
    March 18th 2022, 16:00:17.247	Looking up io.spring.dependency-management:io.spring.dependency-management.gradle.plugin in repository https://repo.maven.apache.org/maven2/	rp/renovate-repro
    March 18th 2022, 16:00:17.247	Looking up not.a.real.dependency:not-real-dep-name in repository https://repo.maven.apache.org/maven2/	rp/renovate-repro
    March 18th 2022, 16:00:17.356	Content is not found for Maven url	rp/renovate-repro
    March 18th 2022, 16:00:17.450	Looking up io.spring.dependency-management:io.spring.dependency-management.gradle.plugin in repository https://plugins.gradle.org/m2/	rp/renovate-repro
    March 18th 2022, 16:00:17.487	Content is not found for Maven url	rp/renovate-repro
    March 18th 2022, 16:00:17.907	Failed to look up dependency not.a.real.dependency:not-real-dep-name	rp/renovate-repro
    March 18th 2022, 16:00:18.527	Found 29 new releases for io.spring.dependency-management:io.spring.dependency-management.gradle.plugin in repository https://plugins.gradle.org/m2/	rp/renovate-repro
    March 18th 2022, 16:00:18.656	Found 57 new releases for org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://repo.maven.apache.org/maven2/	rp/renovate-repro
    March 18th 2022, 16:00:18.719	Looking up org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://plugins.gradle.org/m2/	rp/renovate-repro
    March 18th 2022, 16:00:20.540	Found 115 new releases for org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://plugins.gradle.org/m2/	rp/renovate-repro
    March 18th 2022, 16:00:20.786	Package releases lookups complete	rp/renovate-repro
    March 18th 2022, 16:00:20.851	branchifyUpgrades	rp/renovate-repro
