# Migrating from the Marketplace to Self-Hosted: Step-by-Step Guide

If you've been using Gatling Enterprise from the Marketplace and wish to migrate to a self-hosted instance, follow this comprehensive guide for a seamless transition. Please make sure to have backups of all your data before proceeding.

## Step 1: Preparing the Marketplace Instance

1.1. Stop Gatling Enterprise on the Marketplace instance using the command:
```bash
sudo systemctl stop frontline
```

1.2. Stop the Cassandra database on the Marketplace instance using the command:
```bash
sudo systemctl stop cassandra
```

1.3. Create backups of the following directories on the Marketplace instance:
   - `/var/lib/cassandra`: This contains Cassandra's data.
   - `/opt/frontline/conf` and `/opt/frontline/keys`: These directories hold Gatling Enterprise's configuration.

## Step 2: Setting up the Self-Hosted Instance

2.1. Install Gatling Enterprise with the latest version on the self-hosted instance.

2.2. Stop Gatling Enterprise on the self-hosted instance using the command:
```bash
sudo systemctl stop frontline
```

2.3. Stop the Cassandra database on the self-hosted instance using the command:
```bash
sudo systemctl stop cassandra
```

2.4. Delete the current content inside the `/var/lib/cassandra` folder on the self-hosted instance.

2.5. Copy the previously saved Cassandra data from the Marketplace instance to the self-hosted instance's `/var/lib/cassandra` directory.

2.6. Set appropriate ownership and permissions for the `/var/lib/cassandra` folder using the command:
```bash
sudo chown cassandra:cassandra -R /var/lib/cassandra
```

2.7. Delete the content of the `/opt/frontline/conf` and `/opt/frontline/keys` directories on the self-hosted instance.

2.8. Copy the previously saved Gatling Enterprise configuration from the Marketplace instance to the self-hosted instance's `/opt/frontline/conf` and `/opt/frontline/keys` directories.

2.9. Set appropriate ownership and permissions for the copied directories using the command:
```bash
sudo chown frontline:frontline -R /opt/frontline/conf /opt/frontline/keys
```

## Step 3: Starting the Self-Hosted Instance

3.1. Start the Cassandra database on the self-hosted instance using the command:
```bash
sudo systemctl start cassandra
```

3.2. Wait for a few minutes to allow the Cassandra database to start successfully.

3.3. Start Gatling Enterprise on the self-hosted instance using the command:
```bash
sudo systemctl start frontline
```

3.4. Wait for a few minutes to ensure Gatling Enterprise starts correctly.

Congratulations! You have successfully migrated from the AWS Marketplace to a self-hosted Gatling Enterprise instance. Ensure everything works as expected and verify all your data and configurations are intact.
