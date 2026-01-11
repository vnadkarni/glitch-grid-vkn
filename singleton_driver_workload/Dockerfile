# Start from a thin linux distribution.
FROM docker.io/library/alpine:latest
LABEL maintainer="Antithesis <support@antithesis.com>"

# Make sure to update the current packages, then grab the two programs
# we'll need to have in order for the singleton_driver_workload driver to run.
RUN apk update
RUN apk upgrade
RUN apk add bash curl

# Add source code
ADD singleton_driver_workload.sh .
# Above line can be removed as we're copying the source to the required test directory below.
COPY ./singleton_driver_workload.sh /opt/antithesis/test/v1/main/singleton_driver_workload.sh
RUN chmod 777 /opt/antithesis/test/v1/main/singleton_driver_workload.sh

# Define the entrypoint.
# Make sure to use the array version of this specification, so other command-line
# arguments and parameters can be specified in the Dockerfile.
# ENTRYPOINT [ "/bin/bash", "./singleton_driver_workload.sh" ]
# Above line commented because Entry point for this is set to "sleep infinity" in docker-compose.yml. Alternatively, we can set it here with ENTRYPOINT [ "/bin/bash", "sleep infinity" ]