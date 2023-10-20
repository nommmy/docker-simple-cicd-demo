FROM gradle:7 AS base

# WORKDIR /workspace
# CMD ["./gradlew", "bootRun"]
CMD ["bash"]

# build
FROM base AS test-and-build
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# production
FROM openjdk:17 AS production
COPY --from=test-and-build /workspace/build/libs/api-0.0.1-SNAPSHOT.jsr ./api.jar
CMD ["java", "-jar", "api.jar"]