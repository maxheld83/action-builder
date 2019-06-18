FROM github/docker-tag:1

LABEL "name"="BATS Action Tester"
LABEL "maintainer"="GitHub Actions <support+actions@github.com>"
LABEL "version"="1.0.0"

LABEL "com.github.actions.name"="BATS Action Tester"
LABEL "com.github.actions.description"="Action for testing GitHub Actions"
LABEL "com.github.actions.icon"="check-circle"
LABEL "com.github.actions.color"="gray-dark"
COPY LICENSE README.md THIRD_PARTY_NOTICE.md /

RUN apt-get update && \
    apt-get install --no-install-recommends -y \
        build-essential \
        ca-certificates \
        curl \
        git \
        gnupg2 \
        jq \
        make \
        shellcheck && \
    curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
    apt-get install -y \
        nodejs && \
    npm install -g \
        bats \
        bats-support \
        bats-assert && \
	apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/bin/make"]
CMD ["test"]
