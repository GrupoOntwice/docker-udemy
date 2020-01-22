FROM centos as test

RUN fallocate -l 10M /opt/file1
RUN fallocate -l 20M /opt/file2
RUN fallocate -l 30M /opt/file3

FROM alpine 

COPY --from=test /opt/file2 /opt/myfile