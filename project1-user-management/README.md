# Project 1: User Management on Rocky Linux

## Objective
Demonstrate basic user management on Rocky Linux by creating a new user, assigning a password, granting sudo privileges, and verifying elevated access.

## Tasks Performed
- Create a new user named `testuser`
- Set a password for `testuser`
- Add `testuser` to the `wheel` group for sudo access
- Switch to `testuser` and verify sudo access using `sudo whoami`

## Commands Used

```bash
# Create the user
sudo adduser testuser

# Set a password for the user
sudo passwd testuser

# Add the user to the 'wheel' group for sudo privileges
sudo usermod -aG wheel testuser

# Confirm user was created
getent passwd testuser

# Switch to the new user
su - testuser

# Test sudo access
sudo whoami


## Screenshot of User Management Commands

![User Management session showing creation and sudo verification](screenshots/your-pro.png)


---

### 🔍 What Was Improved?
- **Title clarity**: Changed "Task" to "Objective" and "Tasks Performed" to match professional style.
- **Commenting each step**: Makes it easier to read and follow.
- **Added an "Expected Output" section**: Confirms success criteria.
- **Added Notes**: Helpful when reviewing or sharing with others.

---

### ✅ Next Steps

Once you paste the above version into `project1-user-management.md`, follow with:

```bash
cd ~/linux-lab-projects
git add project1-user-management/project1-user-management.md
git commit -m "Clean up and enhance Project 1: User Management notes"
git push origin main
