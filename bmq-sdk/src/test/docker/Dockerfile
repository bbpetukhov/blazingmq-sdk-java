ARG image
FROM ${image}

ENV BMQ_DOCKER_TMPDIR=/tmp/bmq-broker

RUN mkdir -p /tmp/cores

COPY config/ /etc/local/bmq/

EXPOSE 30114
 
# RUN echo "/usr/local/bin/bmqbrkr /etc/local/bmq &" > /tmp/startup.sh
RUN echo "sleep 12345 &" > /tmp/startup.sh
RUN echo "BROKER_PID=$!" >> /tmp/startup.sh
RUN echo "sleep 5" >> /tmp/startup.sh
RUN echo "kill -QUIT $BROKER_PID" >> /tmp/startup.sh
RUN echo "sleep 5" >> /tmp/startup.sh
RUN echo "cat /proc/sys/kernel/core_pattern" >> /tmp/startup.sh
RUN echo "ls -lah /tmp/cores" >> /tmp/startup.sh
RUN echo "cat /proc/sys/kernel/core_pattern > /tmp/cores/sample.txt" >> /tmp/startup.sh
RUN echo "ls -lah /tmp/cores" >> /tmp/startup.sh
RUN chmod +x /tmp/startup.sh
CMD ["/tmp/startup.sh"]

# CMD [ "/usr/local/bin/bmqbrkr"  \
#     , "/etc/local/bmq"          \
#     ]
