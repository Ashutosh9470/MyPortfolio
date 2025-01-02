import os
import subprocess

# Define the repository path and README file location
repo_path = "path/to/your/portfolio-website-repo"  # Replace with the actual path to your repo
readme_path = os.path.join(repo_path, "README.md")

# Define the content to add to the README.md file
update_content = """
## Portfolio Website

This repository contains the source code for my personal portfolio website. It showcases my projects, skills, and achievements.

### Features
- Fully responsive design
- Showcases projects like Spotify Clone, Weather Clone, and more
- Contact form to reach out to me

### Technologies Used
- HTML, CSS, JavaScript
- [React.js](https://reactjs.org/) (if applicable)
- Backend: Flask/Django/Node.js (if applicable)

### Live Demo
Check out the live demo here: [Your Portfolio Website](https://your-portfolio-website-link.com)  

Feel free to explore and give feedback!
"""

# Write the content to the README.md file
try:
    with open(readme_path, "w") as readme_file:
        readme_file.write(update_content)
    print("README.md updated successfully.")
except Exception as e:
    print(f"Error updating README.md: {e}")

# Git commands to commit and push the changes
def git_command(command, cwd):
    try:
        result = subprocess.run(command, cwd=cwd, text=True, capture_output=True, check=True)
        print(result.stdout)
    except subprocess.CalledProcessError as e:
        print(f"Error executing {command}: {e.stderr}")

# Stage the changes
git_command(["git", "add", "README.md"], cwd=repo_path)

# Commit the changes
git_command(["git", "commit", "-m", "Updated README.md with Portfolio Website details"], cwd=repo_path)

# Push the changes
git_command(["git", "push"], cwd=repo_path)

print("Changes pushed to GitHub successfully.")
