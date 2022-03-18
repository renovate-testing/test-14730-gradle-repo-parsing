# Reproduction for Gradle Project in Renovate

This project uses gradle and demonstrates that the `repositories` block in build.gradle with a custom repo specified is being ignored by Renovate.

When I build, here is the output, showing that gradle is looking for my custom (fake) repository:

    $ ./gradlew build
    > Task :compileJava FAILED

    FAILURE: Build failed with an exception.

    * What went wrong:
    Execution failed for task ':compileJava'.
    > Could not resolve all files for configuration ':compileClasspath'.
       > Could not resolve not.a.real.dependency:not-real-dep-name:1.2.3.
         Required by:
             project :
          > Could not resolve not.a.real.dependency:not-real-dep-name:1.2.3.
             > Could not get resource 'https://renovate-reproduction-test.io/repository/not/a/real/dependency/not-real-dep-name/1.2.3/not-real-dep-name-1.2.3.pom'.
                > Could not GET 'https://renovate-reproduction-test.io/repository/not/a/real/dependency/not-real-dep-name/1.2.3/not-real-dep-name-1.2.3.pom'.
                   > renovate-reproduction-test.io

    * Try:
    > Run with --stacktrace option to get the stack trace.
    > Run with --info or --debug option to get more log output.
    > Run with --scan to get full insights.

    * Get more help at https://help.gradle.org

    BUILD FAILED in 1s
    1 actionable task: 1 executed


When Renovate runs however, it ignores the repository setting and looks only at Maven Central and the Gradle Plugin repos respectively. Here are the relevant logs from Renovate's run of this project (self-hosted docker, repo in bitbucket).

    March 18th 2022, 16:00:17.247	rp/renovate-repro	Found gradle-wrapper package files
    March 18th 2022, 16:00:17.247	rp/renovate-repro	Found 3 package file(s)
    March 18th 2022, 16:00:17.247	rp/renovate-repro	Dependency extraction complete
    March 18th 2022, 16:00:17.247	rp/renovate-repro	Looking up org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://repo.maven.apache.org/maven2/
    March 18th 2022, 16:00:17.247	rp/renovate-repro	Looking up io.spring.dependency-management:io.spring.dependency-management.gradle.plugin in repository https://repo.maven.apache.org/maven2/
    March 18th 2022, 16:00:17.247	rp/renovate-repro	Looking up not.a.real.dependency:not-real-dep-name in repository https://repo.maven.apache.org/maven2/
    March 18th 2022, 16:00:17.356	rp/renovate-repro	Content is not found for Maven url
    March 18th 2022, 16:00:17.450	rp/renovate-repro	Looking up io.spring.dependency-management:io.spring.dependency-management.gradle.plugin in repository https://plugins.gradle.org/m2/
    March 18th 2022, 16:00:17.487	rp/renovate-repro	Content is not found for Maven url
    March 18th 2022, 16:00:17.907	rp/renovate-repro	Failed to look up dependency not.a.real.dependency:not-real-dep-name
    March 18th 2022, 16:00:18.527	rp/renovate-repro	Found 29 new releases for io.spring.dependency-management:io.spring.dependency-management.gradle.plugin in repository https://plugins.gradle.org/m2/
    March 18th 2022, 16:00:18.656	rp/renovate-repro	Found 57 new releases for org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://repo.maven.apache.org/maven2/
    March 18th 2022, 16:00:18.719	rp/renovate-repro	Looking up org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://plugins.gradle.org/m2/
    March 18th 2022, 16:00:20.540	rp/renovate-repro	Found 115 new releases for org.springframework.boot:org.springframework.boot.gradle.plugin in repository https://plugins.gradle.org/m2/
    March 18th 2022, 16:00:20.786	rp/renovate-repro	Package releases lookups complete
