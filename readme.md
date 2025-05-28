# Dotfiles


2.  **Clone the bare repository:**
    ```bash
    git clone --bare git@github.com:connorkeevill/dotfiles.git $HOME/.dotfiles
    ```

3.  **Define the `dotfiles` alias in your new shell:**
    To interact with the cloned bare repository, you need the `config` alias. Since your actual `.zshrc` (or `.bashrc`) containing the alias definition is not yet checked out and active, you need to define it manually for the current session:
    ```bash
    alias dotfiles='/usr/bin/git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'
    ```
    *(This alias is temporary for this session. It will become permanent once the shell configuration file is checked out and sourced).*

4.  **Check out your dotfiles:**
    This command populates your home directory with the files from the repository.
    ```bash
    dotfiles checkout
    ```
    * **Important:** You might encounter an error if default configuration files (e.g., a default `.zshrc` or `.bash_profile` provided by the OS) already exist in your home directory. The error message will typically list the files that would be overwritten.
    * **To resolve this:** Manually back up these conflicting files (e.g., `mv ~/.zshrc ~/.zshrc.backup_os_default`) or delete them if you are sure you don't need them. Then, run `config checkout` again. You might need to use `config checkout -f` to force the checkout, but use this with caution.

5.  **Reload shell configuration:**
    ```bash
    source ~/.zshrc  # Or source ~/.bashrc, etc.
    ```
