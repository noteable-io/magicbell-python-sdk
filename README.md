# MagicBell-Python

<img src="./assets/MB_logo_Purple_2800x660.png" width="50%">

This SDK provides convenient access to the [MagicBell REST API](https://magicbell.com/docs/rest-api/overview) from applications written in Python. It includes helpers for creating notifications, managing users, managing projects, and GraphQL.

This is an unofficial Python SDK for [MagicBell](https://magicbell.com) open sourced with ❤️ by <a href="https://noteable.io">Noteable</a>, a collaborative notebook platform that enables teams to use and visualize data, together.

[Install](#installation) | [Getting Started](#getting-started) | [Examples](./examples) | [License](./LICENSE) | [Code of Conduct](./CODE_OF_CONDUCT.md) | [Contributing](./CONTRIBUTING.md)


## Requirements

Python 3.8+

## Installation

### Poetry

```shell
poetry add magicbell
```

Then import the package:

```python
import magicbell
```

### Pip
```shell
pip install magicbell
```

Then import the package:

```python
import magicbell
```

## Getting Started

```python
import magicbell
from magicbell.configuration import Configuration

config = Configuration(
    api_key="YOUR_API_KEY",
    api_secret="YOUR_API_SECRET",
)
async with magicbell.MagicBell(config) as mb:
    # Send a notification
    await mb.realtime.create_notification(
        magicbell.WrappedNotification(
            notification=magicbell.Notification(
                title="My first notification from python!",
                recipients=[magicbell.Recipient(email="dan@example.com")],
            )
        )
    )
```

### Authentication

Most API calls require your MagicBell project API Key and API Secret.
Some API calls (i.e. projects) require your MagicBell user JWT (enterprise only).

See the [MagicBell API documentation](https://www.magicbell.com/docs/rest-api/reference#authentication) for more information.

### Configuration

Configuration can be done explicitly using the `magicbell.Configuration` class,
or implicitly by setting environment variables with the `MAGICBELL_` prefix.

#### Explicit Configuration

```python
from magicbell.configuration import Configuration


# Create a configuration object with the required parameters
config = Configuration(
    api_key="YOUR_API_KEY",
    api_secret="YOUR_API_SECRET",
)
```

#### Implicit Configuration

```shell
export MAGICBELL_API_KEY="YOUR_API_KEY"
export MAGICBELL_API_SECRET="YOUR_API_SECRET"
```

```python
from magicbell.configuration import Configuration


config = Configuration()
```

### Examples

For more examples see the [`examples` directory](./examples).

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

-------

<p align="center">Open sourced with ❤️ by <a href="https://noteable.io">Noteable</a> for the community.</p>

<img href="https://pages.noteable.io/private-beta-access" src="./assets/noteable.png" alt="Boost Data Collaboration with Notebooks">

