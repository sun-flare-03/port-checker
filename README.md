# port-checker

[![Build Status](https://img.shields.io/github/actions/workflow/status/user/port-checker/ci.yml?branch=main)]()
[![Go Version](https://img.shields.io/badge/go-1.22+-blue.svg)]()
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

Network port scanner and service discovery tool with JSON output — designed for production workloads with a focus on reliability and developer ergonomics.

## Features

- Zero Dependencies: No external packages required for core functionality
- Graceful Shutdown: Clean shutdown handling with configurable drain timeout
- Structured Logging: Built-in structured logging with slog compatibility

## Getting Started

### Installation

```bash
go get github.com/user/port-checker@latest
```

## Usage

```go
package main

import (
	"fmt"
	"github.com/user/port-checker"
)

func main() {
	client := portchecker.New(
		portchecker.WithTimeout(30 * time.Second),
	)

	result, err := client.Run(context.Background())
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println(result)
}
```

## Configuration

Configuration can be provided via environment variables, a config file, or programmatically.

| Variable | Description | Default |
|----------|-------------|--------|
| `PORT_CHECKER_TIMEOUT` | Request timeout in seconds | `30` |
| `PORT_CHECKER_RETRIES` | Number of retry attempts | `3` |
| `PORT_CHECKER_LOG_LEVEL` | Log verbosity (debug, info, warn, error) | `info` |

## Contributing

Contributions are welcome! Please read the [contributing guidelines](CONTRIBUTING.md) before submitting a pull request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
