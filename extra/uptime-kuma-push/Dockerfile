FROM golang:1.22-bookworm AS build
WORKDIR /src
COPY uptime-kuma-push.go .
RUN CGO_ENABLED=0 go build -o /uptime-kuma-push uptime-kuma-push.go

FROM debian:bookworm-slim AS release
RUN useradd --create-home kuma
USER kuma
WORKDIR /home/kuma
COPY --from=build /uptime-kuma-push ./uptime-kuma-push

ENTRYPOINT ["/home/kuma/uptime-kuma-push"]


