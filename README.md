---

# GitHub List Users with Read Access Script

This bash script helps you list users who have read access to a specified GitHub repository. It uses the GitHub API to get the list of collaborators with read access (pull permission) to the repository.

## Prerequisites

Before you can run the script, ensure you have the following:

1. **GitHub Account**: You need a GitHub account with the necessary permissions to access the repository.
2. **Personal Access Token (PAT)**: Create a GitHub personal access token with at least `repo` and `read:org` scope to authenticate and interact with the GitHub API.
3. **`jq` Installed**: The script uses `jq` to parse JSON responses. Install it using the following command:
   ```bash
   sudo apt-get install jq
   ```

## Script Overview

The script performs the following tasks:
- Takes two command-line arguments: the owner of the repository and the name of the repository.
- Authenticates with the GitHub API using your GitHub username and personal access token.
- Fetches the list of collaborators with read access (pull permission) to the specified repository.
- Displays the list of users who have read access to the repository.

## Usage

### Command-Line Arguments
- `<repository_owner>`: The owner of the GitHub repository (e.g., `octocat`).
- `<repository_name>`: The name of the GitHub repository (e.g., `Hello-World`).

### Running the Script
To use the script, run the following command:

```bash
./github_list_read_users.sh <repository_owner> <repository_name>
```

#### Example:
```bash
./github_list_read_users.sh octocat Hello-World
```

### Output:
The script will list the users who have read access to the specified repository:

```
Users with read access to octocat/Hello-World:
user1
user2
user3
```

If no users with read access are found, it will display:

```
No users with read access found for octocat/Hello-World.
```

## Error Handling

If you miss the required arguments, the script will display an error message and usage instructions:

```
Error: Missing arguments.
Usage: ./github_list_read_users.sh <repository_owner> <repository_name>
Example: ./github_list_read_users.sh octocat Hello-World
```

## Script Structure

1. **GitHub API Authentication**:  
   The script uses basic authentication with your GitHub username and personal access token to authenticate API requests.

2. **Listing Collaborators**:  
   The script sends a GET request to the GitHub API to fetch the list of collaborators for the specified repository and filters users who have read access.

3. **Error Handling**:  
   If the repository or collaborators cannot be fetched, the script provides clear error messages.

4. **Helper Function**:  
   The `display_usage` function is used to display instructions for running the script correctly if the user doesn't provide the necessary arguments.

## Dependencies

- `curl`: A tool for transferring data with URLs (usually pre-installed on most systems).
- `jq`: A lightweight and flexible command-line JSON processor.

### Installation of Dependencies

On Ubuntu/Debian systems, you can install `curl` and `jq` using the following commands:
```bash
sudo apt-get update
sudo apt-get install curl jq
```

## License

This script is provided as-is. Feel free to fork and modify it according to your needs.

---

### Notes:
1. Make sure to replace `$username` and `$token` in the script with your GitHub username and personal access token.
2. You may consider adding your GitHub username and token as environment variables for better security.

