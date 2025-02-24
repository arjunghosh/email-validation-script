# Email Validation Bash Script for Termux

## 🌟 Project Overview

This comprehensive email validation script is designed specifically for Termux, providing a robust solution for verifying email addresses through multiple validation stages.

## 🚀 Features

- **Multi-Stage Validation**
  - Regex-based format checking
  - DNS MX record lookup
  - SMTP protocol verification

- **Termux-Optimized**
  - Mobile-friendly script
  - Lightweight and efficient
  - Easy to install and use

## 🛠 Prerequisites

- Termux installed on Android device
- Basic understanding of bash scripting
- Active internet connection

## 📦 Installation

1. Update Termux packages:
   ```bash
   pkg update
   ```

2. Install required dependencies:
   ```bash
   pkg install dnsutils
   pkg install swaks
   pkg install netcat
   ```

3. Clone the repository:
   ```bash
   git clone https://github.com/arjunghosh/email-validation-script.git
   cd email-validation-script
   ```

4. Make scripts executable:
   ```bash
   chmod +x CRUD_Run_check_email.sh
   chmod +x check_email_validity.sh
   ```

## 🔍 Usage

### Basic Validation
```bash
./check_email_validity.sh email@example.com
```

### Multiple Email Validation
```bash
./check_email_validity.sh email1@example.com email2@example.com
```

## 🧪 Testing

Run the comprehensive test suite:
```bash
./test_suite.sh
```

## 🔧 Configuration

- Edit `config.conf` to customize validation parameters
- Adjust timeout values
- Configure logging preferences

## 🛡️ Error Handling

The script provides comprehensive error messages:
- Format validation errors
- DNS resolution issues
- SMTP connection problems

## 📊 Logging

- Automatic log generation
- Configurable log rotation
- Detailed error tracking

## 🚧 Troubleshooting

Common issues and solutions are documented in the script's comments and comprehensive documentation.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📄 License

[Specify your license here - e.g., MIT License]

## 🌐 Contact

Arjun Ghosh
- GitHub: @arjunghosh
- Email: arjun.ghosh81@gmail.com

## 📚 Documentation

For a detailed guide on email validation, script architecture, and advanced usage, refer to the comprehensive documentation in the repository.

---

**Disclaimer**: This script is for educational and testing purposes. Always respect email server policies and terms of service.
