# Configuration Guide

This document describes how to structure and use the configuration file for this project.

## Config File Structure

The application uses a JSON-based configuration file to manage settings. Below is the documented structure:

### Basic Example

```json
{
  "app": {
    "name": "Hunt D3 Fixture",
    "version": "1.0.0",
    "environment": "development"
  },
  "database": {
    "host": "localhost",
    "port": 5432,
    "name": "hunt_d3",
    "user": "app_user",
    "password": "${DB_PASSWORD}"
  },
  "server": {
    "port": 3000,
    "host": "0.0.0.0",
    "debug": true
  },
  "features": {
    "enableLogging": true,
    "enableCache": false
  }
}
```

## Configuration Fields

### App Section
- **name** (string): Application name
- **version** (string): Application version
- **environment** (string): Current environment (`development`, `staging`, `production`)

### Database Section
- **host** (string): Database server hostname or IP
- **port** (number): Database server port
- **name** (string): Database name
- **user** (string): Database user credentials
- **password** (string): Database password (use environment variables for security)

### Server Section
- **port** (number): Port for the application to listen on
- **host** (string): Host address to bind to
- **debug** (boolean): Enable debug mode

### Features Section
- **enableLogging** (boolean): Enable application logging
- **enableCache** (boolean): Enable caching functionality

## Environment Variables

For sensitive data like passwords, use environment variables instead of hardcoding values:

```json
{
  "database": {
    "password": "${DB_PASSWORD}"
  }
}
```

Then set the environment variable before running the application:

```bash
export DB_PASSWORD=your_secure_password
```

## Creating Your Config

1. Copy the example structure above
2. Modify values according to your environment
3. For production, ensure sensitive values are stored as environment variables
4. Place the config file in the project root or specify its path via `CONFIG_PATH` environment variable

## Environment-Specific Configs

You can maintain separate config files for different environments:
- `config.development.json`
- `config.staging.json`
- `config.production.json`

The application will load the appropriate file based on the `NODE_ENV` environment variable.
