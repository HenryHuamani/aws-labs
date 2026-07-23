# Commands

## Update system

```bash
sudo dnf update -y
```

## Install Apache

```bash
sudo dnf install -y httpd
```

## Enable Apache

```bash
sudo systemctl enable httpd
```

## Start Apache

```bash
sudo systemctl start httpd
```

## Verify Apache

```bash
sudo systemctl status httpd
```

## Test locally

```bash
curl http://localhost
```