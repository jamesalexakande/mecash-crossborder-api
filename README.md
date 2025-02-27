# Introduction 
This repository contains the official API documentation for meCash's Cross-Border Payment API. Ihe documentation provides a clear and concise guide for developers to integrate the API seamlessly. 

## About the API
The meCash Cross-Border Payment API enables secure international money transfers between a sender and a recipient. The documentation covers:

- Request structure and required parameters

- Response details (success and error responses)

- Example API requests and responses.
  
## Files in this Repository
- [API_Documentation.md](API_Documentation.md) - Detailed documentation of the Crossborder API endpoint, request/response structure, and error handling
- [README.md](README.md) - This file, providing a general overview of the repository and instructions on how to access the documentation.

## Viewing the Documentation
**To view the API documentation remotely:**
1. Navigate to the [API_Documentation.md](API_Documentation.md) file in this repository.
2. The documentation is written in Markdown format and can be viewed directly on GitHub or any Markdown-compatible viewer.

**To view locally:**
Open Terminal (Mac) or Powershell (Windows) and navigate to the desired directory you want to clone the repository in 

- Clone the repository to your local machine:

  `git clone https://github.com/yourusername/mecash-crossborder-api.git`

- Navigate to the cloned folder after the cloning process is complete 

  `cd mecash-crossborder-api`

- Open API_Documentation.md in a Markdown viewer or editor like VS Code.

## Implementation Notes
- The API uses RESTful principles with JSON request/response formats
- Authentication is required via Bearer token in the Authorization header
- Rate limiting is implemented (100 requests per minute per API key)

## Contributions
If you’d like to contribute or suggest improvements, feel free to submit a pull request or open an issue.

## Support
For any inquiries or support, reach out to meCash Support at support@me-cash.com

## License
This project is licensed under the MIT License.


