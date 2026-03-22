# Email Deliverability Checklist for `diahub.dk`

Set these DNS records in your DNS provider:

## SPF

```txt
Type: TXT
Host: @
Value: v=spf1 include:_spf.google.com ~all
```

Use the include from your real email provider if not Google Workspace.

## DKIM

Create DKIM records from your mail provider admin panel (selector + public key).

Example format:

```txt
Type: TXT
Host: selector1._domainkey
Value: v=DKIM1; k=rsa; p=...
```

## DMARC

```txt
Type: TXT
Host: _dmarc
Value: v=DMARC1; p=none; rua=mailto:hello@diahub.dk; fo=1; adkim=s; aspf=s
```

After monitoring reports, move to stricter policy:

1. `p=quarantine`
2. `p=reject`
