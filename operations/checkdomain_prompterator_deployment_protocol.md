# Checkdomain Deployment Protocol — Prompterator

**Artifact ID:** KOS-OPS-0001  
**System:** Prompterator / KnowledgeOS / Operator Fischer  
**Artifact Type:** Deployment Protocol / Troubleshooting Note  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  

---

## 1. Situation

Prompterator `index.html` was prepared locally on the Mac and copied to Desktop:

```text
~/Desktop/index.html
```

GitHub source:

```text
fissafissaintoki/gosseos-framework/demos/operator-fischer-proof-of-work-demo/site/index.html
```

Target live path at checkdomain:

```text
/htdocs/index.html
```

---

## 2. Critical UI Clarification

The checkdomain page `Paketdomains verwalten` with:

```text
Verwendung: Nutzung im Webhosting-Paket (Verzeichnis)
Verzeichnis: /htdocs
```

is **not** the upload page.

It only confirms that the domain points to `/htdocs`.

Required next step after confirming/saving:

```text
Back to Webhosting overview → find Dateimanager / WebFTP / Webspace / FTP-Zugang → open /htdocs → upload index.html
```

---

## 3. Correct Click Path

Expected path:

```text
checkdomain Login
→ Webhosting
→ Webhosting-Paket / Verwaltung
→ Dateimanager or WebFTP
→ htdocs
→ replace index.html
```

Avoid:

```text
Domains
DNS
E-Mail
SSL
Weiterleitungen
Nameserver
Paketdomains verwalten as final stop
```

---

## 4. Upload Rule

Inside `/htdocs`:

1. Rename old `index.html` to `index.backup.html` if possible.
2. Upload `~/Desktop/index.html`.
3. Ensure final name is exactly:

```text
index.html
```

---

## 5. Live Verification

Open:

```text
https://prompterator.de?fresh=1
```

Expected markers:

```text
Prompterator MVP v4
Intent-to-Artifact Routing aktiv
Rohinput rein. Konkretes Artefakt raus.
```

---

## 6. Recovery Note

If Dateimanager/WebFTP is not visible, search checkdomain UI for:

```text
Dateimanager
WebFTP
Webspace
FTP-Zugänge
Dateien verwalten
```

If only domain-management items are visible, user is in the wrong section.

---

## 7. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Deployment confusion documented: Paketdomains page confirms `/htdocs` mapping but is not file upload interface. | Operator Fischer |
