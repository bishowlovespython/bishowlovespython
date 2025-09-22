# Automation & Scripting

Python is one of the best languages for automating repetitive tasks, writing scripts, and managing system operations. Its simplicity, cross-platform support, and rich standard library make it a favorite for DevOps, sysadmins, and everyday power users.

## ⚙️ Key Applications

- **Task Automation**: Rename files, convert formats, scrape websites, generate reports, etc.
- **System Administration**: Monitor servers, manage processes, clean logs, and automate backups.
- **File & Directory Operations**: Search, create, move, or organize files and folders.
- **Web Automation**: Automate form submissions, web scraping, and browser actions.
- **Remote Server Management**: SSH into servers, run commands, and automate deployments.
- **Scripting CI/CD Pipelines**: Automate testing, builds, and deployments.

## 🛠️ Common Libraries & Tools

| Library      | Purpose                                  |
| ------------ | ---------------------------------------- |
| `os`         | Interacting with the operating system    |
| `subprocess` | Running shell commands                   |
| `shutil`     | File operations (copy, move, etc.)       |
| `glob`       | Pattern matching for filenames           |
| `pathlib`    | Object-oriented file path handling       |
| `pyautogui`  | GUI automation (mouse, keyboard control) |
| `schedule`   | Task scheduling for automation scripts   |
| `paramiko`   | SSH and SFTP for remote automation       |
| `selenium`   | Browser automation                       |
| `requests`   | HTTP requests for APIs and web scraping  |

## 🤖 Example Use Cases

- Rename and organize downloaded files automatically
- Backup important files daily to a cloud or external drive
- Monitor server disk usage and send alerts
- Automatically scrape and email a daily weather report
- Fill out web forms or scrape data from websites
- Run tests and deploy code to production on commit

## 🧪 Sample Script: Rename All `.txt` Files in a Folder

```python
import os

folder_path = './documents'
for filename in os.listdir(folder_path):
    if filename.endswith('.txt'):
        new_name = filename.replace(' ', '_')
        os.rename(
            os.path.join(folder_path, filename),
            os.path.join(folder_path, new_name)
        )
```

---

## 📚 Learning Resources

- [Automate the Boring Stuff with Python](https://automatetheboringstuff.com/)
- [Python Standard Library Documentation](https://docs.python.org/3/library/)
- [Real Python – Automation Tutorials](https://realpython.com/tutorials/automation/)
- [PyAutoGUI Documentation](https://pyautogui.readthedocs.io/)
- [Selenium with Python](https://selenium-python.readthedocs.io/)

---

> **Tip**: Start small! Even a short script to clean filenames or send email alerts can save hours over time.
