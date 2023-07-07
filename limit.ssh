#!/bin/bash
# Set the maximum allowed concurrent connections
MAX_CONNECTIONS=1
# Get the currently logged-in user from PAM_USER environment variable
CURRENT_USER="$PAM_USER"
# Check if the current user is root
if [ "$CURRENT_USER" = "root" ]; then
  # Allow root user to have unlimited concurrent connections
  exit 0
fi
# Check if the current user is online
LIVE_CONNECTIONS=$(ps -u "$CURRENT_USER" | grep "sshd" | wc -l)
# Compare the number of live connections with the maximum allowed connections
if [ "$LIVE_CONNECTIONS" -ge "$MAX_CONNECTIONS" ]; then
  # Deny access if the number of live connections exceeds the maximum allowed
  echo "Maximum concurrent connections reached. Access denied."
  exit 1
else
  # Allow access if the number of live connections is within the allowed limit
  exit 0
fi
