FROM public.ecr.aws/docker/library/amazoncorretto:11-alpine
ARG AWS_REGION
ENV AWS_REGION=$AWS_REGION
#https://docs.aws.amazon.com/codeguru/latest/profiler-ug/enabling-the-agent-with-command-line.html
RUN mkdir -p /opt/target
RUN apk update && apk add wget
RUN apk add libcrypto3=3.0.8-r0 libssl3=3.0.8-r0
EXPOSE 8080 5005
COPY target/aws-proserve-java-greeting.war /opt/target/
WORKDIR /opt/target
USER nobody
CMD ["sh", "-c", "java -jar aws-proserve-java-greeting.war --debug"]
HEALTHCHECK CMD curl --fail http://localhost:8080/hello || exit 1