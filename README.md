<div align="center">

# 🧪 Serverest API Tests

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![JSON](https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

*Complete collection of automated tests for Serverest API validation*

[Get Started](#-installation) • [Documentation](#-main-test-scenarios) • [Usage](#-how-to-run-the-tests) • [License](#-license)

</div>

---

## 📋 Overview

This project contains a comprehensive collection of automated tests to validate the main endpoints of the **Serverest** public API (https://serverest.dev/). The tests were developed using Postman with focus on:

- Contract validation (schema validation)
- Status code, payload and response time verification
- Organization by resources (Users, Login, Products, Cart)
- Automated execution via Collection Runner
- CI/CD integration (GitHub Actions)

## 🎯 Objectives

- Demonstrate proficiency in API testing using Postman
- Implement rigorous contract validation (Schema Validation)
- Organize tests in a structured and reusable way
- Apply test automation best practices
- Properly document tests and processes

## 🌐 API Under Test

**Serverest**: https://serverest.dev/

A free REST API that simulates an online store, providing endpoints for:
- User management
- Login and authentication system
- Product catalog
- Shopping cart

## 📁 Project Structure

```
api-test-serverest/
├── Serverest_API_Tests.postman_collection.json
├── Serverest_Environment.postman_environment.json
├── LICENSE
├── evidencias/
│   └── exemplo_resultado_execucao.json
└── README.md
```

## 🚀 Installation

### Prerequisites
- **Postman**: Version 9.0+
- **Git**: For version control

### Import Collection and Environment

1. Open Postman
2. Click **Import** in the top menu
3. Select the files:
   - `Serverest_API_Tests.postman_collection.json`
   - `Serverest_Environment.postman_environment.json`
4. Make sure the **"Serverest - Environment"** is selected

## 💻 Usage

### Running via Collection Runner

1. Right-click on the **"Serverest API Tests"** collection
2. Select **"Run collection"**
3. Recommended settings:
   - **Environment:** Serverest - Environment
   - **Iterations:** 1
   - **Delay:** 1000ms (to avoid rate limiting)
4. Click **"Run Serverest API Tests"**


## 🧪 Main Test Scenarios

### Users
- **GET All Users**: Validates structure, quantity and required fields
- **GET Single User**: Verifies specific data and integrity
- **POST Create User**: Tests creation with response validation
- **POST Create User with Duplicate Email**: Tests error handling
- **GET Non-existent User**: Validates 404 error handling

### Authentication
- **POST Login Success**: Tests authentication with valid credentials
- **POST Login Failure**: Tests authentication with invalid credentials

### Products
- **GET All Products**: Validates structure and format
- **GET Single Product**: Verifies product data
- **POST Create Product**: Tests product creation (authenticated)
- **POST Create Product Unauthorized**: Tests access control

### Cart
- **GET All Carts**: Validates cart structure
- **POST Create Cart**: Tests cart creation
- **DELETE Cancel Purchase**: Tests cart cancellation

### Test Statistics
- **Total Requests**: 15
- **Total Assertions**: 45+
- **Resource Coverage**:
  - Users: 5 tests
  - Login: 2 tests
  - Products: 4 tests
  - Cart: 3 tests

### Example Results
```json
{
  "totalTests": 15,
  "passedTests": 14,
  "failedTests": 1,
  "testPassPercentage": 93.33,
  "averageResponseTime": 279
}
```

📁 **Evidence available at:** `/evidencias/exemplo_resultado_execucao.json`

## 🔍 Validations Implemented

### Basic Validations
- **Status Codes**: 200, 201, 400, 401 as expected
- **Response Time**: Maximum 2000ms for all operations
- **Content-Type**: JSON headers verification
- **Required Fields**: Presence of essential properties

### Advanced Validations
- **Schema Validation**: Using integrated validation library
- **Data Types**: Validation of types (string, number, boolean)
- **Format Validation**: Emails, URLs, complex structures
- **Relationship Validation**: Correct relationship IDs

### Business Validations
- **Array Lengths**: Expected number of items
- **Data Integrity**: Consistency between related resources
- **Field Constraints**: Minimum values, specific formats

## 📋 Environment Variables

| Variable | Value | Description |
|----------|-------|-------------|
| `baseUrl` | `https://serverest.dev` | API base URL |
| `auth_token` | Generated via login | Authentication token |
| `usuario_id` | Dynamic | User ID for tests |
| `produto_id` | Dynamic | Product ID for tests |
| `carrinho_id` | Dynamic | Cart ID for tests |

## 🏆 Main Highlights

### Organization
- **Hierarchical structure**: Folders organized by resource
- **Clear naming**: Descriptive and standardized names
- **Separation of responsibilities**: Each folder with specific purpose

### Test Quality
- **Comprehensive coverage**: All main endpoints covered
- **Multiple validations**: Multiple checks per request
- **Error cases**: Tests for failure scenarios

### Automation
- **Reusable scripts**: Consistent test logic
- **Dynamic variables**: Shared data between tests
- **Batch execution**: Ability to run entire suite

### Reports
- **Detailed results**: Complete information about each test
- **Performance metrics**: Response time and statistics
- **Data export**: Exportable results for analysis

## 🛠️ Technologies and Tools

- **Postman**: Main tool for API testing
- **JavaScript**: Language for test scripts and validations
- **JSON**: Data format for collections and environments
- **GitHub Actions**: CI/CD automation

## 📊 Project Statistics

- **Total Requests**: 15 endpoints tested
- **Validations per Request**: 3-5 tests per endpoint
- **Resource Coverage**: 4 different resources (Users, Login, Products, Cart)
- **Operation Types**: GET, POST, DELETE
- **Error Scenarios**: Validation of 401, 404 and duplicate cases

## 🎓 Best Practices and Learnings

### Implemented
- **Structured organization** of tests by resource
- **Rigorous validation** of API contracts
- **Complete automation** with JavaScript scripts
- **Integrated documentation** in Postman itself
- **Code reuse** with environment variables
- **Error scenario handling**

### Development Process
1. **API Analysis**: Study of Serverest documentation
2. **Planning**: Definition of test structure
3. **Implementation**: Creation of requests and scripts
4. **Validation**: Testing and refinement of validations
5. **Documentation**: Creation of complete documentation
6. **Versioning**: Organization for collaboration

## 🔄 Continuous Integration

The project includes a CI/CD pipeline configured to automatically validate files:

- **Triggers**: Push, Pull Request, Manual execution
- **Environment**: Ubuntu Latest
- **Validations**: JSON syntax, collection structure, environment configuration
- **Reports**: Detailed summary in GitHub Actions

📁 **Configuration**: `.github/workflows/postman-tests.yml`

## 🔧 Troubleshooting

### Common Issues

#### Error: "Cannot read property 'split' of undefined"
**Solution**: Check if the "Serverest - Environment" is selected and the `baseUrl` variable is defined. The collection includes automatic validations that set the baseUrl if it doesn't exist.

#### Error: "Variable baseUrl is not defined"
**Solution**: The collection has automatic validation that sets `baseUrl = https://serverest.dev` if the variable doesn't exist. Check the Postman Console for detailed logs.

#### Error: "Request failed with status code 401"
**Solution**: First run the "POST - Login Success" test to generate the necessary authorization token.

## 📞 Support

For questions or issues:
- Check the Postman Console for detailed logs
- Review the Serverest API documentation
- Check execution logs in GitHub Actions

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

## 🤝 Contribution

This project was developed as a demonstration of skills in:
- **Automated API testing**
- **Contract validation**
- **Test project organization**
- **Technical documentation**
- **Development best practices**

## 📄 License

This project is under the MIT license. See the [LICENSE](LICENSE) file for more details.

## 👤 Author

<div align="center">

**Anthony Coelho**

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/anthonycdp)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/anthonycoelhoqae/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:anthonycoelho.dp@hotmail.com)

*QA Engineer specialized in performance testing and automation*

</div>

---

<div align="center">

### If this project was useful to you, consider giving it a star!

### Contributions are welcome!

**Version**: 1.0.0

</div>