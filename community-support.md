## 19. Community & Support

Linux Lite is more than just a lightweight operating system—it's also supported by a vibrant, helpful community of users, contributors, and developers. Whether you're a beginner or an experienced Linux user, there are several channels through which you can get help, contribute back, and stay engaged with the project.

---

### 19.1 Forums

The [Linux Lite Forums](https://www.linuxliteos.com/forums/) are the primary place for asking questions, sharing tips, reporting issues, and participating in community discussions.

#### How to Ask for Help

Before posting, always search the forum to see if your question has already been answered. If not, create a new topic with the following best practices:

* Use a **clear and specific title** (e.g., “Wi-Fi not connecting after update”)
* Include relevant **system information**:

  * Linux Lite version (`Menu > System Information`)
  * Hardware specs
  * Error messages or logs
* Explain **what you've already tried**
* Be **polite and patient**—this is a volunteer-run community

To post:

1. Register on the forum (free account)
2. Choose the appropriate board (e.g., “Newbie - Help me”, “Hardware”, “Software”)
3. Create your post and follow up if someone responds

Common Help Topics:

* Installing software
* Boot and install issues
* Printer/scanner setup
* Graphics or sound problems
* Updating and upgrading

#### Reporting Bugs

If you believe you've found a bug:

1. Try to reproduce the issue on a clean boot
2. Make sure your system is up to date:

   ```bash
   sudo apt update && sudo apt upgrade
   ```
3. Gather the following:

   * System info (`inxi -Fxz`)
   * Logs from `/var/log/`, dmesg, or journalctl
   * Screenshots or error messages

Then:

* Post a detailed report in the **“Bugs”** section of the forum
* Check if the bug is related to a known upstream package (e.g., Ubuntu or Debian)

Constructive, well-documented reports help the Linux Lite team improve the system for everyone.

---

### 19.2 Social Channels

Linux Lite maintains an active presence on several platforms where users can interact, get quick help, or follow updates.

#### Reddit

The [r/LinuxLite](https://www.reddit.com/r/LinuxLite/) subreddit is an informal community for discussions, news, troubleshooting, and sharing Linux Lite experiences.

* Ask quick questions
* Share screenshots or success stories
* Discuss software recommendations

#### Telegram

Linux Lite has a user-managed **Telegram group** for real-time support and general chat.

To join:

* Search for “Linux Lite” on Telegram, or
* Find a link on the official website/forum

Note: Telegram is community-driven and not officially moderated by the Linux Lite development team.

#### Facebook

There is an active [Linux Lite Facebook Group](https://www.facebook.com/groups/linuxlite) where users can connect, ask questions, and share updates.

* Suitable for casual discussions and beginner questions
* Posts are moderated to ensure a respectful environment

---

### 19.3 Contributing

Linux Lite welcomes contributors from all backgrounds. Whether you're a translator, tester, writer, or developer, there are several ways to get involved.

#### Translating

Help make Linux Lite accessible in your native language by contributing to translations.

* Visit the [Linux Lite Translation Portal](https://www.transifex.com/linux-lite/)
* Sign up and choose your language
* Start translating phrases used in the system, Welcome screen, Lite Tools, etc.

Translation helps new users around the world get started in their own language.

#### Testing

Become part of the testing team and provide feedback on upcoming versions.

* Participate in **Release Candidate (RC)** testing before major releases
* Report bugs or glitches via the forum
* Test across various hardware configurations and use cases

This helps ensure stability and polish before public release.

#### Wiki Editing

Contribute to the Linux Lite Wiki by improving existing pages or adding new content.

* Correct outdated instructions
* Add step-by-step guides or troubleshooting tips
* Use proper formatting (Markdown or HTML depending on platform)

If the wiki is hosted on GitHub or a platform like MkDocs:

* Fork the repository
* Make edits
* Submit a pull request

Otherwise, contact the documentation maintainers via the forum for permission to contribute.

---

