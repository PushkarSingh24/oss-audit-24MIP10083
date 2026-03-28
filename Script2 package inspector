#!/bin/bash
# Script 2: FOSS Package Inspector (Clean Version)

PACKAGE="code"

echo "Checking package: $PACKAGE"
echo "--------------------------"

# Check if VS Code is installed
if command -v code &> /dev/null; then
    echo "VS Code is installed."

    # Show version
    code --version | head -n 1

    # Show path
    echo "Location: $(which code)"
else
    echo "VS Code is NOT installed."
fi

# Case statement
case $PACKAGE in
    code) echo "VS Code: a lightweight, extensible open-source editor" ;;
    git) echo "Git: version control system built for collaboration" ;;
    nginx) echo "Nginx: high-performance web server" ;;
    python) echo "Python: powerful open-source programming language" ;;
    *) echo "Unknown package" ;;
esac
