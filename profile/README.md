<div align="center">
  <img src="https://raw.githubusercontent.com/sentinel-app-io/.github/main/profile/logo.png" width="80" height="80" alt="Sentinel" />
  <h1>Sentinel</h1>
  <p><strong>Know when your services break — before your users do.</strong></p>
  <p>
    Ingest health signals from any system. Get alerted instantly.<br/>
    Track uptime over time. Simplified monitoring for SaaS.
  </p>
  <br/>
  <a href="https://sentinel-app.io">Website</a> ·
  <a href="https://app.sentinel-app.io">App</a> ·
  <a href="https://app.sentinel-app.io/docs">Docs</a>
</div>

---

## What is Sentinel?

Sentinel is a health signal hub. Instead of running heavy agents or complex infrastructure, you push a lightweight signal from wherever your service runs — and Sentinel handles the rest.

```bash
curl -X POST https://app.sentinel-app.io/api/v1/signals/ \
  -H "STNL-Access-Key: $KEY_ID" \
  -H "STNL-Secret-Key: $SECRET" \
  -d '{"service": "payment-api", "status": 1}'
```

That's it. Your service is created automatically on first signal. No setup, no manifests, no dashboards to configure.

---

## Features

**Source-agnostic** — Accept signals from CI pipelines, cron jobs, Prometheus exporters, Grafana alerts, or any custom script. One endpoint, any source.

**Instant alerts** — Get notified on Slack, email, or webhook the moment a service degrades or goes down.

**Kubernetes-native** — Deploy the operator once, annotate your workloads. Sentinel monitors Deployments, StatefulSets and DaemonSets and reports up / degraded / down states in real time.

**SLA tracking** — Define uptime commitments and track compliance over time. Know your error budget at a glance.

**Auto-discovery** — Services are created automatically on first signal. No manual setup needed.

## Kubernetes operator

One operator per cluster. No sidecars. No per-pod overhead.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: payment-api
  annotations:
    sentinel.io/monitor: "true"
    sentinel.io/service: "payment-api"
```

```bash
kubectl apply -f https://raw.githubusercontent.com/sentinel-app-io/sentinel-k8s-operator/main/manifests/install.yaml
```

→ [sentinel-app-io/sentinel-k8s-operator](https://github.com/sentinel-app-io/k8s-operator)

---

## Works with any language

Send a signal in one HTTP call — from any stack.

<table>
<tr>
<td><b>Python</b></td>
<td>

```python
requests.post(url, headers={
    "STNL-Access-Key": KEY_ID,
    "STNL-Secret-Key": SECRET,
}, json={"service": "my-api", "status": 1})
```

</td>
</tr>
<tr>
<td><b>Go</b></td>
<td>

```go
req, _ := http.NewRequest("POST", url, body)
req.Header.Set("STNL-Access-Key", keyID)
req.Header.Set("STNL-Secret-Key", secret)
http.DefaultClient.Do(req)
```

</td>
</tr>
</table>

See the [full documentation](https://app.sentinel-app.io/docs) for examples in JavaScript, Rust, Ruby, and more.

---

<div align="center">
  <a href="https://app.sentinel-app.io">Get started free</a>
</div>
