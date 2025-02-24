#!/bin/bash

# Check for required commands
command -v nslookup >/dev/null 2>&1 || { echo "Error: nslookup required. Install dnsutils."; exit 1; }

check_email() {
    email="$1"
    
    # Basic format validation with improved regex
    if [[ ! "$email" =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
        echo "✗ Invalid email format: $email"
        echo "Email should:"
        echo "- Contain only letters, numbers, and allowed special characters (._%+-)"
        echo "- Have a valid domain with at least one dot"
        echo "- Not contain spaces"
        return 1
    fi

    domain=$(echo "$email" | cut -d'@' -f2)
    echo "Checking domain: $domain"
    
    # DNS lookup with 5 second timeout and better error handling
    echo "Looking up MX records..."
    mx_records=$(timeout 5 nslookup -type=mx "$domain" 2>/dev/null | grep "mail exchanger")
    if [ $? -eq 124 ]; then
        echo "✗ Lookup timeout for domain: $domain"
        return 2
    elif [[ -z "$mx_records" ]]; then
        echo "✗ No MX records found for $domain"
        return 1
    fi

    # Handle known email providers with improved messages
    case "$domain" in
        *gmail.com|*googlemail.com)
            echo "✓ Gmail domain verified"
            echo "MX Records found:"
            echo "$mx_records" | sed 's/^/  /'  # indent MX records
            echo "Note: Gmail address validation complete (domain-level only)"
            return 0
            ;;
        *yahoo.com|*yahoo.*)
            echo "✓ Yahoo domain verified"
            echo "MX Records found:"
            echo "$mx_records" | sed 's/^/  /'
            echo "Note: Yahoo address validation complete (domain-level only)"
            return 0
            ;;
        *hotmail.com|*outlook.com|*live.com|*microsoft.*)
            echo "✓ Microsoft domain verified"
            echo "MX Records found:"
            echo "$mx_records" | sed 's/^/  /'
            echo "Note: Microsoft address validation complete (domain-level only)"
            return 0
            ;;
        *)
            echo "✓ Domain verification successful"
            echo "MX Records found for $domain:"
            echo "$mx_records" | sed 's/^/  /'
            echo "Note: Basic domain verification complete. Cannot verify individual mailbox."
            return 0
            ;;
    esac
}

# Check arguments
if [[ -z "$1" ]]; then
    echo "Usage: $0 <email_address>"
    echo "Example: $0 user@example.com"
    exit 1
fi

# Run check with timing information
echo "Starting email validation at $(date '+%H:%M:%S')"
check_email "$1"
exit_code=$?
echo "Validation completed at $(date '+%H:%M:%S')"

# Provide clear exit status
case $exit_code in
    0) echo "Final Status: ✓ Validation successful" ;;
    1) echo "Final Status: ✗ Validation failed" ;;
    2) echo "Final Status: ! Timeout occurred" ;;
esac

exit $exit_code
